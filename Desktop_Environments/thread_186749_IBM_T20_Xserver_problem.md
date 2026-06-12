---
title: "IBM T20 Xserver problem"
date: 2006-06-02
forum: Desktop Environments
---

### Post by dlai on 2006-06-02
Hi everyone I have a problem with my ibm t20. only 1/20 times the xserver will let me get into GDM... it is not possible to change terminal either with Ctrl+Alt+F"X" ... Anyone had the same problem? please help...

---

### Post by jrei on 2006-06-03
I had the same problem.

I removed the 'splash ' option from the kernel options within the '/boot/grub/menu.lst' and till now it worked fine. Be aware that you have to remove it also from the
```

# defoptions= ...

```
otherwise it will be added to your boot line every time grub resets the config. This will happen for example if you get a new kernel version with an upgrade.

Greetings, Jörn

---

### Post by jrei on 2006-06-03
take a look at:
[http://ubuntuforums.org/showthread.php?p=1085982#post1085982](http://ubuntuforums.org/showthread.php?p=1085982#post1085982)

---

### Post by jrei on 2006-06-03
The spalsh seems to be not the reason. 

Since I noticed that the X failures allways hapend when I had a mouse connected i thought the xorg.conf could be the problem.
I checked the 'xorg.conf' and noticed that the synapics touchpad was loaded as an input device. 
I removed that section and the entry in the serverlayout section.
Works till now.

Greetings, Jörn

PS: 'noapic' is needed by the ethernet device of the T20. Sorry for suggesting it.

---

### Post by dlai on 2006-06-04
Hey Jörn thank you very much for your response... i tried adding both acpi=off and noapic to my boot command, in my menu.lst in /boot/grub... but it does not work, did i do it correctly, or do you have any other ideas??

---

### Post by mitya89 on 2006-06-26
I believe I am having this same or a similar problem on my IBM Thinkpad T22. Ubuntu 6.06 boots up fine, then all I see is a flashing terminal underscore character, which eventually stops flashing and the computer seems to freeze. Once in many restarts, GDM will load properly and everything is fine from there on. (BTW, I had mo problems like this with Breezy 5.10)

Sometimes I still here the login ready sound even though I can't see anything, but it is still impossible to do anything. This problem doesn't seem related to the mouse, although I did remove all refrences to the synap. touchpad and tablet pc controls as refrenced earlier in this post, to no avail.

I'm not sure what to do since this seems to be a GDM, not X, problem. when I disabled GDM thru the terminal in recovery mode (give root password for maint.)```
update-rc.d -f gdm remove
```
I can still log into X with startx, no problem.

I would really like to get GDM working again, but im thinking of installing KDM because this problem is just so wierd and intermittent.
-mitya

---

### Post by mitya89 on 2006-06-26
I take that back. i think it is an X problem. i tried startx at a terminal after i disabled GDM and got the same underscore on the screen, computer frozen.

---

### Post by Sandu on 2006-06-27
[QUOTE=mitya89]I believe I am having this same or a similar problem on my IBM Thinkpad T22. Ubuntu 6.06 boots up fine, then all I see is a flashing terminal underscore character, which eventually stops flashing and the computer seems to freeze. Once in many restarts, GDM will load properly and everything is fine from there on. (BTW, I had mo problems like this with Breezy 5.10)

[/QUOTE]

I have the same problem on my Thinkpad T22. In 9 from 10 times system hangs just before GDM start. Problem have appeared after updating. 
Clean install from 6.06 CD have worked fine.

I think problem is in "savage" driver (because it was updated).

---

### Post by dlai on 2006-06-28
Found the solution look [here]("http://ubuntuforums.org/showthread.php?t=205411&highlight=ibm+t20")

---

