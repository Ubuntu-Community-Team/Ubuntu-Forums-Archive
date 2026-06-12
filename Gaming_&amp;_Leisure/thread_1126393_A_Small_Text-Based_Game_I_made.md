---
title: "A Small Text-Based Game I made"
date: 2009-04-15
forum: Gaming &amp; Leisure
---

### Post by Swenghk on 2009-04-15
I've been learning Python for about a week now and I made this simple, boring, and dry, text-based game. I just wanted to do something fun and time consuming (despite its simplicity... I'm still new to this you know!)

It is attached below.

---

### Post by benj1 on 2009-04-15
think it might be better being called rat attack ;)

seriously tho good effort if youve only been coding for a week. 

if your asking for constructive criticism i only found one bug (non serious) the rat has 8 hp but says at the start it has 10.
i probably wouldn't have menuchoose() call itself, i would probably have a while loop
ie 
```
while menu1 != "3": 
```
i would probably also be a bit more thorough and flexible with accepting options.
but carry one with the good work look forward to adventure 2 :p

---

### Post by Swenghk on 2009-04-15
I'm sorry for my noobishness, but how could you turn:

```
def menuchoose():
    print """
1. Fight
2. Stats
3. Quit
"""
    menu1 = raw_input("What will you choose? ")
    if menu1 == "1":
        fightmenu()
    elif menu1 == "2":
        statsmenu()
    elif menu1 == "3":
        quitmenu()
    else:
        print "What? Numerical values only please..."
        menuchoose()
```

into a while loop?

---

### Post by benj1 on 2009-04-15
somthing like

```
def menuchoose():
    print """
1. Fight
2. Stats
3. Quit
"""
while True:   
    menu1 = raw_input("What will you choose? ")
    if menu1 == "1":
        fightmenu()
    elif menu1 == "2":
        statsmenu()
    elif menu1 == "3":
        quitmenu()
    else:
        print "What? Numerical values only please..."
```



its not really a problem on smaller scripts, but could cause problems with larger scripts

---

### Post by tcoffeep on 2009-04-15
Just to point a small problem out : 
```

What will you choose? 2
Traceback (most recent call last):
  File "Adventure.py", line 196, in <module>
    maingame()
  File "Adventure.py", line 80, in maingame
    introgame()
  File "Adventure.py", line 104, in introgame
    menuchoose()
  File "Adventure.py", line 177, in menuchoose
    fightmenu()
  File "Adventure.py", line 43, in fightmenu
    menuchoose()
  File "Adventure.py", line 177, in menuchoose
    fightmenu()
  File "Adventure.py", line 43, in fightmenu
    menuchoose()
  File "Adventure.py", line 177, in menuchoose
    fightmenu()
  File "Adventure.py", line 43, in fightmenu
    menuchoose()
  File "Adventure.py", line 179, in menuchoose
    statsmenu()
  File "Adventure.py", line 188, in statsmenu
    print "Health: " + str(health)
NameError: global name 'health' is not defined

```

pops up when i select stats.

Otherwise, great effort. :)

---

### Post by Swenghk on 2009-04-16
Omg! That's what i have been looking for this whole time! You are a god benji1!!!!!!

---

### Post by Swenghk on 2009-04-16
Could you just please explain to me how that works? I don't want to use it not knowing how it works...

---

### Post by tcoffeep on 2009-04-16
I think health is set as a local variable ( I'm not very savvy on Python programming ), so it doesn't carry into other functions. Try declaring health as a global variable.

---

### Post by wsonar on 2009-04-16
I'm going to get into python after I finish c++ I know I should have done vice versa but 6 one way half a dozen another..

I'll grab this and check it out

---

### Post by Swenghk on 2009-04-16
A REALLY good book is Python Programming For The Absolute Beginner...

I can send you the .chm file...(Am I allowed to do that?)

---

### Post by tcoffeep on 2009-04-16
( i don't suggest making that offer over the forums. )

---

### Post by benj1 on 2009-04-17
> **Swenghk said:**
> Omg! That's what i have been looking for this whole time! You are a god benji1!!!!!!

why thankyou :D

if youre asking how the while loop works

```
while True:
```
is basically a infinite loop (because its always true) so you do need to make sure you break out, i just did it instead of usinging it to check the value of menu1. if you have a look in the programming talk stickies it will give you links to a few good books and websites.

---

### Post by zenlunatic on 2009-04-18
I downloaded the script.  How do you run it?  I gave execute permission to user and did ./Adventure.py

---

### Post by tcoffeep on 2009-04-18
you run 

python Adventure.py

---

### Post by calrogman on 2009-04-18
> You step into the arena and prepare to fight the rat...
Your Weapon: Iron Sword
Begin!
=======================================================
HP: 10
Rat HP: 10
The rat attacks you for 4 points of damage!
HP:  6
Rat Health:  8
Press enter...
You swing your sword for 2 points of damage!
HP:  6
Rat Health:  6
Press enter...
The rat attacks you for 3 points of damage!
HP:  3
Rat Health:  6
Press enter...
You swing your sword for 4 points of damage!
HP:  3
Rat Health:  2
Press enter...
The rat attacks you for 4 points of damage!
HP:  -1
Rat Health:  2
Press enter...
You swing your sword for 4 points of damage!
HP:  -1
Rat Health:  -2
Press enter...
You killed the rat!
Press enter to continue...

> You swing your sword for 5 points of damage!
HP:  2
Rat Health:  1
Press enter...
The rat attacks you for 2 points of damage!
HP:  0
Rat Health:  1
Press enter...
You swing your sword for 2 points of damage!
HP:  0
Rat Health:  -1
Press enter...
You killed the rat!


Seems your variable checking could do with some work.
O_o

---

### Post by calrogman on 2009-04-18
> **tcoffeep said:**
> you run 

python Adventure.py

Or add
```
#!/usr/bin/env python
```
at the top of the script.

---

### Post by Swenghk on 2009-04-18
Yeah, I spent 15 minutes trying to figure out hpw to get the variables right in the battle block. I just couldn't figure it out...I thought I could turn each turn into a function, but that would be cumbersome

---

