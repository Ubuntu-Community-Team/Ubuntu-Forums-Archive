---
title: "Black menu/windows bug"
date: 2010-05-03
forum: Desktop Environments
---

### Post by Eonfge on 2010-05-03
Hello everybody,

I´m relatively new to Ubuntu and although I am very aducuate with computers it self (technology studie; modding, scripting and programming) I found a truly atrocious bug that ****s up Gnome (I assume).

Here is a screenshot: 
[http://img689.imageshack.us/img689/4342/blackscreenmenubug.png](http://img689.imageshack.us/img689/4342/blackscreenmenubug.png)

The install is from one month ago, and since then i upgrades to 10.04. I never did any unusual stuff as far as I know. I added a few private repository&#347; (playdeb, Virtualbox and some PPA´s) and configurated Compiz so it´s good  to impress my class mates. This all is installed on a HP Pavilion DV6 with a Ati Graphics card and proprietary drivers.

Hopefully it´s some very simple thing that you can spell out for me cause I´m not in a great deal of time fixing this ****. Considering I nead this PC for school: it must work. Booting in windows would be a sign of weakness towards my classmates and it´s no good advertising for linux in general.

Please help me if you can, and forgive me if I didn´t search good enough, but google and launchpad didn´t help.

---

### Post by nerdy_kid on 2010-05-03
are you running compiz? try turning off desktop effects (right click desktop bottom entry, then last tab in the dialog that pops up).  what graphics card are you using?

---

### Post by Eonfge on 2010-05-03
He, thanks for the attention,

I have an Ati Mobile HD 4650. I will try to turn off compiz, I´m not sure if it helps though and even if it does, I want to use compiz for quick, easy and nice window management. It´s one of the best thing Linux has to offer.

Edit:

I have made a new profile, turned compiz to default and then reconfigured it. I will tell you tomorrow how it works out, but I am sceptical. The bug occurred very often, mostly when changing screens while browsing/typing and watching video. So if there is someone who had this as well, or who knows what´s going on, please tell.

---

### Post by nerdy_kid on 2010-05-03
you dont really have to create a new account, but i suppose it doesnt matter :)

yeah ive heard of simalar issues with ati cards, a line added to your xorg file fixes it.

are you using the restricted  drivers?

---

### Post by Eonfge on 2010-05-04
> 
This all is installed on a HP  Pavilion DV6 with a Ati Graphics card and proprietary drivers.

restricted/proprietary, I use the official drivers from Ati.

Could you tell me what I should add to the Xorg files? Resetting all compiz settings is no problem, but it's not likely to make any difference.

---

### Post by nerdy_kid on 2010-05-04
> **Eonfge said:**
> restricted/proprietary, I use the official drivers from Ati.

Could you tell me what I should add to the Xorg files? Resetting all compiz settings is no problem, but it's not likely to make any difference.

oh wow cant believe i didnt see that sorry :-/

no first please run
```

metacity --replace

```
in a terminal.  I have to go digging for what line to add in the xorg file and *need* to know if turning off compiz fixes it first.

---

### Post by Eonfge on 2010-05-05
He, i've done it and far Two things have changed: 
First off. My screenlets appeared back on screen (tomboy/dead flower). When i started up, I saw black shapes (like the bug) appear but then the screenlets disappeared again. Now they are back and running accordingly. 

All compiz settings are changed to default. They now override my fency configurations. I assume this was intended but I assume that it's restores it self when I close the session.

---

### Post by denham2010 on 2010-05-05
If you are using a default install of compiz, it seems likely that emerald (the compiz window decorator) is crashing, hence why you get everything back when starting metacity.

The 'flash' effect you get on start up would likely be compiz starting, trying to run emerald, which then crashes, and then metacity starts and takes over.

If you go into CCSM, you can change the default decorator to metacity and prevent the 'flash' effect on startup.

Of course, you could also open a terminal and enter
```
emerald --replace
```
to see if emerald really is the problem.

Cheers.

---

### Post by Eonfge on 2010-05-05
He, 

I've been looking to metacity / compiz and I also followed your advice to that emerald might be crashing. 

Problem is, when i did --replace it told me that it was not installed. I installed it with apt-get and when I run it, it changes the windows manager as well. Becouse the change went flawless, and even more so, I didn't have it at first, Emerald doesn't seem the be the problem.

i also figured out how to turn on compiz, in 'appearence' I had to set it to full effects

---

