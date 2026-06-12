---
title: "i lost window borders w/ effects enabled"
date: 2008-06-29
forum: Desktop Environments
---

### Post by PLANETARY on 2008-06-29
hello I am new to linux. i just got my system running all happy today (7.10) i had my effects turned on extra and decided to try to suspend the computer and return later. well it seemed to shut down but didnt turn off, i hit keys to wake it up and waited but no response. i turned it off and restarted it later to find that i have no window borders. the only way i get them is with effects turned off. i tried the default depth to 24 but it was already there i also tried metacity -- replace but i still cant get the effects to work properly. i also tried different themes. i dont have any effects programs or anything. this system is a coppermine P3 with a geforce3 and a gig of ram.
thanks

---

### Post by bwang on 2008-06-29
Open a terminal and execute:
```
sudo apt-get install emerald
```
Then enable Compiz and hit Alt+F2. Type:
```
emerald --replace
```
and see if that works.

---

### Post by PLANETARY on 2008-06-29
ok i installed emerald (what is emerald?) tho i dont know what you mean 'enable compiz' (what is compiz?) i searched around 
does this thread help
[http://ubuntuforums.org/showthread.php?t=601310](http://ubuntuforums.org/showthread.php?t=601310)

---

### Post by James_the_dude on 2008-06-29
You may have already tried this, but have you gone to "Advanced Desktop Effects Settings" in you system preferences (if you don't see it you can install it, search for "compizconfig-settings-manager", this is a graphical front-end to tweak compiz settings to your liking), and then went to "window decoration" and checked to see if it is enabled?

---

### Post by PLANETARY on 2008-06-30
ok in installed compiz and emerald, it would only allow me to select custom effects with the window decorator disabled. i still cant get the window border even if i turn window decor on and off.

---

### Post by smo0th on 2008-06-30
same thing here, I installed the "Advanced Desktop Effects Settings" GUI from Applications>>Add/Remove to tweak compiz effects and somehow the borders dissapear out of nothing and in the middle of nowhere, I tried to reset it  by unselecting and selecting the borders option in the GUI but got no luck, right now I'm working without borders moving the windows by right-clicking the application and selecting Move from the bottom bar, anyway, de-selecting to use borders and restarting the X server should work.

---

### Post by PLANETARY on 2008-06-30
i didnt get that last part

---

### Post by dtach on 2008-06-30
this just happened to me, you should download "advanced desktop effects settings" from the add/remove software button.

once you download it, it will show under system preferences.

go to it and look under "effects". 

now uncheck "reflection" if its checked.

thats the effect that made all my borders dissapear. and then stupid me made the effect apply to the windows too, and that almost really ****** me over...

---

### Post by PLANETARY on 2008-07-02
well whatever, i just reinstalled it. works fine!

---

