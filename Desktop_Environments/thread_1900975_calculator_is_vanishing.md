---
title: "calculator is vanishing"
date: 2011-12-27
forum: Desktop Environments
---

### Post by suv27 on 2011-12-27
I am using my first Ubuntu 11.04/Linux on my desktop for the past around four months. I made it dual boot with XP and I hardly use XP. Till yesterday (26/12/2011) night everything was fine, but  yesterday , instead of opening the calculator from Application>Accessories>calculator I tried to open it from the keyboard, it showed up a couple of times and suddenly it just started vanishing . I can see it appearing on the desktop like a flash of light and just disappearing somewhere which I cant figure out and just a few hours back I downloaded and installed Network Traffic Monitor from source forge and placed it on the extreme left corner of the top panel and when I tried to open it by double clicking it behaved exactly like the calculator . SOMEBODY PLZ HELP ME GET BACK MY CALCULATOR AND Ntm :(

---

### Post by IWantFroyo on 2011-12-27
Try opening them in a terminal. This should give you some error messages if something's wrong with the program.

```
gcalc
```

I don't know the command for NTM. You might have to open Alacarte and check the command (assuming NTM is in your menus).

---

### Post by suv27 on 2011-12-28
> **IWantFroyo said:**
> Try opening them in a terminal. This should give you some error messages if something's wrong with the program.

```
gcalc
```

I don't know the command for NTM. You might have to open Alacarte and check the command (assuming NTM is in your menus).
Thanks for the suggestion buddy but "gcalc" didn't, help wish I could catch hold of a veteran in this game. If u  know somebody plz forward it to him/her.

---

### Post by utnubuuser on 2011-12-28
run ps -A in a terminal after launching calculator to see if it's actually running, or if it is crashing immediately...

ps -A | grep gcalc

ps. unrelated though significant, check out qalculate ( [http://sazeit.com/articles/qalculate!]("http://sazeit.com/articles/qalculate!") ) 
It's a waaaayyyy better calculator than gcalc

---

### Post by suv27 on 2011-12-29
> **utnubuuser said:**
> run ps -A in a terminal after launching calculator to see if it's actually running, or if it is crashing immediately...

ps -A | grep gcalc

ps. unrelated though significant, check out qalculate ( [http://sazeit.com/articles/qalculate!]("http://sazeit.com/articles/qalculate!") ) 
It's a waaaayyyy better calculator than gcalc
Hi mate I tried out your suggestion and it showed soooo....   many things being a newbie I got puzzled and had to run for cover and my problem lies unsolved but I am taking a look at qalculate

---

