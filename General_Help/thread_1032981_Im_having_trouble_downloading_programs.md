---
title: "Im having trouble downloading programs"
date: 2009-01-06
forum: General Help
---

### Post by tgm1220 on 2009-01-06
ok im new to ubuntu and im having trouble downloading basic programs like a flashplayer bc everytime i go to download it i get an error message that says only one software management tool is allowed to be run at a time but there ar e no other software management systems open.  it also says please close update manager synaptic or aptitude first.  I have 8.10 and Id like some help please

---

### Post by 2hot6ft2 on 2009-01-06
Close synaptic, close add/remove apps, if you have the orange or red icon on the right side in the top taskbar click on it and install those updates first since that means update manager is running if it's showing. That icon means there are updates for your computer.

After you install all the updates it will go away and you can install other things. And you're wanting flash player, java and all the other nice multimedia stuff do this to get them.

Put this in a terminal and hit Enter (you can copy and paste if you want)
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

When it returns to the prompt (something@something $) it will be done and you can close it.

---

### Post by tgm1220 on 2009-01-06
i closed all that stuff but then when i try to run the update manager i get this -
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
???

---

### Post by tuxxy on 2009-01-06
> **tgm1220 said:**
> i closed all that stuff but then when i try to run the update manager i get this -
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
???

Open a terminal and enter the following command then retry

```
sudo dpkg --configure -a
```

---

### Post by 2hot6ft2 on 2009-01-06
Hey tuxxy, when we get this one fixed up I would like to know how to fix this one. [http://ubuntuforums.org/showthread.php?t=1032912](http://ubuntuforums.org/showthread.php?t=1032912)
Nevermind he's gone offline.

---

### Post by tuxxy on 2009-01-06
> **2hot6ft2 said:**
> Hey tuxxy, when we get this one fixed up I would like to know how to fix this one. [http://ubuntuforums.org/showthread.php?t=1032912](http://ubuntuforums.org/showthread.php?t=1032912)
Nevermind he's gone offline.

Sure Ill head over there now :D

---

