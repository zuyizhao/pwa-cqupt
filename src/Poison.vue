<template>
  <blockquote class="ui-poison">
    <p>{{result}}</p>
  </blockquote>
</template>

<script>
import util from '@/util'
export default {
  name: 'poison',
  data: function () {
    return {
      result: null,
      bag: ['花有重开日，人无再少年',
        '能在一分钟左右做完的事情，就不要拖延，立即去完成。',
        '如果只看合乎自己口味的书，那你永远只能知道你已经知道的事。——蔡康永',
        '重复的事，一定很无聊吗？ 太阳每天升起一次，降下一次，确实是非常重覆的事， 但我还是动不动就被日出和夕阳给打动啊。——蔡康永',
        '要么庸俗，要么孤独。——叔本华',
        '是金子，早晚会发光。是石头，到哪里都不会发光。就算你是金子，早晚也会花光。',
        '很多时候，乐观的态度和好听的话帮不了你。为什么不问问朋友呢？',
        '“为什么我总是感觉自己特别普通?”“可能是因为你确实比较普通吧。”',
        '不要说生活伤害了你，其实生活压根不知道你是谁。',
        '你如果不会思考，你连成功它爸是谁都不知道。',
        '孩子，我要求你读书用功，不是因为我要你跟别人比成绩，而是，我希望你将来会拥有选择的权利，选择有意义、有时间的工作，而不是被迫谋生。当你的工作在你心中有意义，你就有成就感。当你的工作给你时间，不剥夺你的生活，你就有尊严。成就感和尊严，给你快乐。龙应台《亲爱的安德烈》',
        '那些明亮的人，如果与你相遇，你是否有与之相匹配的分量。',
        '世上本无事，庸人自扰之。',
        '努力和遗憾，哪个更让人痛苦？——凯尔特人队训',
        '如果你要安排计划，请从终点开始安排。',
        '你全力做到的最好，可能还不如别人随便搞搞。但是你还年轻啊~',
        '[毒]生活不止眼前的苟且还有你到不了的远方和读不懂的诗。',
        '[毒]岁月是把杀猪刀，那是对好看的人说的，长得丑的，岁月拿他一点办法都没有。',
        '[毒]你必须非常努力，才能相信自己是无能为力。',
        '[毒]只要肯努力，没有什么事情是搞不砸的。',
        '[毒]加油，你是最胖的。',
        'Happiness = Reality - Expectation',
        '很多东西都是遗传，你能做的，就是变异。',
        '怀疑所有没有思考过和没有证据的东西。',
        '你只有很努力，才能表现的毫不费力。',
        '如果有人被你吸引，他们在与你谈话时，眼睛会比平常更闪烁。',
        '为了在他人的脑海中种植一个想法的种子，应该要求他们不要想到某个特定的事情。',
        '信心的关键是走进一个房间，并假设每个人都喜欢你。',
        '[毒]努力不一定成功，但不努力一定会  很 ~ 轻 ~ 松 ~ 哦 (๑•̀ω•́๑)  ——匿名'
      ]
    }
  },
  created: function () {
    this.openTheBox()
  },
  methods: {
    yogurt: function () {
      let radomIndex = Math.floor(Math.random() * this.bag.length)
      return this.bag[radomIndex]
    },
    choseAnotherFood: function (yogurt, taste) {
      util.getHitokoto(function (err, res) {
        if (err) {
          taste(yogurt)
        } else {
          if (res.hitokoto) {
            taste(res.hitokoto + '  ——' + res.from)
          } else {
            taste(yogurt)
          }
        }
      })
    },
    taste: function (something) {
      this.result = something
    },
    openTheBox: function () {
      var _this = this
      var lucky = Math.random() > 0.3
      if (lucky) {
        this.choseAnotherFood(this.yogurt(), function (finalChoice) {
          _this.taste(finalChoice)
        })
      } else {
        this.taste(this.yogurt())
      }
    }
  }
}
</script>
<style>
.ui-poison {
  text-align: left;
  max-width: 768px;
}

@media screen and (min-width:768px) {
  .ui-poison {
    margin: 20px auto;
    text-align: center
  }
}
</style>
