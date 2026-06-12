---
title: "Remove Launcher"
date: 2011-11-26
forum: Desktop Environments
---

### Post by leilton on 2011-11-26
I think this has been asked before, but every answer I've seen does not work.

"How do you remove the Launcher from the Desktop, (and no Login out and then in under Classic does not do it, nor do any of the other solutions or ways of logging in),"

"As a supplement to the above, once the dreadful thing is gone, how do I get the menu panel back on the top, it disappeared at the time I regretfully applied the Launcher."

To think I tried for ages to get it, then when I do, it just sits and will not, under any circumstances, move, fade or whatever.   Please Please someone know the answer.   At present only thing I can think of is reinstall, and that I really want to avoid.

Long winded I know, but driving me up the wall.

---

### Post by LinuxFan999 on 2011-11-26
Which version of Ubuntu are you using?

---

### Post by BC59 on 2011-11-26
If I understood well you need the old Gnome working, then from a terminal:

```
sudo apt-get install gnome-session-fallback
```

After that to use it logout- choose Gnome Classic- logon

For more tricks and solutions to this:

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by leilton on 2011-11-27
> **LinuxFan999 said:**
> Which version of Ubuntu are you using?
Hi,

Version is Ubuntu 11.4

---

### Post by leilton on 2011-11-27
> **BC59 said:**
> If I understood well you need the old Gnome working, then from a terminal:

```
sudo apt-get install gnome-session-fallback
```

After that to use it logout- choose Gnome Classic- logon

For more tricks and solutions to this:

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)
Hi,

Am complete novice, so, enough that I can give response to suggested command 

,edward@edward-AMILO-PRO-V2030:~$ sudo apt-get install gnome-session-fallback
[sudo] password for edward: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-session-fallback
edward@edward-AMILO-PRO-V2030:~$ 

but not enough to know what next.

Now going to view web site suggested.

---

### Post by MG&amp;TL on 2011-11-27
Ignore the gnome-session fallback then, although that is correct for 11.10.

The way to do it is by logging in, I'm afraid. There should be a box at the bottom, saying 'Unity' or 'Ubuntu' or 'Ubuntu3d'. Click on it, and set it to 'Ubuntu Classic' or 'Gnome'

I hope it helps.

---

### Post by leilton on 2011-11-27
```

For LinuxFan 999
BC 59
MG&TL

May I thank you all for your very prompt response to my problem.

No I don't know how it happened, and keeping my fingers crossed it lasts, but at present the panel is actually moving out of the way and coming back when I point into the far corner.

No done nothing have no done before, appears I'm back to running as 2D.

Many many thanks for all your help.

Tony
```

Hope done this correctly at least.

---

### Post by MG&amp;TL on 2011-11-27
Thank you. (touched). Not many people say thanks as nicely.
Hope you got your problem solved, whatever it might have been.

---

