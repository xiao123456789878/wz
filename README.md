import random

# 定义英雄类
class Hero:
    def __init__(self, name, hp, damage):
        self.name = name
        self.hp = hp
        self.damage = damage

    def attack(self, target):
        damage = random.randint(0, self.damage)
        print(f"{self.name}对{target.name}造成了{damage}点伤害！")
        target.take_damage(damage)

    def take_damage(self, damage):
        self.hp -= damage
        if self.hp <= 0:
            print(f"{self.name}被击败了！")
        else:
            print(f"{self.name}剩余{self.hp}点生命值。")

# 创建两个英雄
hero1 = Hero("孙悟空", 100, 20)
hero2 = Hero("鲁班七号", 120, 18)

# 战斗
while hero1.hp > 0 and hero2.hp > 0:
    attacker = random.choice([hero1, hero2])
    target = hero1 if attacker == hero2 else hero2
    attacker.attack(target)

# 判断胜负
if hero1.hp <= 0:
    print("鲁班七号获胜！")
elif hero2.hp <= 0:
    print("孙悟空获胜！")
