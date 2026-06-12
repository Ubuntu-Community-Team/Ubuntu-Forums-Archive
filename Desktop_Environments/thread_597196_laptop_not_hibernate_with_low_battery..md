---
title: "laptop not hibernate with low battery."
date: 2007-10-30
forum: Desktop Environments
---

### Post by gaiterin on 2007-10-30
Hi!
	
I setup my laptop nx7300HP to hibernate when the battery is at a critical level.

But the laptop not hibernate. When it is no longer battery, it turns off abruptly.

I changed the setup in the configuration editor / apps / gnome-power-manager / thresholds:
Percentage_action 5
Percentage_critical 5
Percentage_low 5

And / apps / gnome-power-manager / general:
Use_time_for_policy Uncheck.

And still does not work (laptop hibernate if I go from the menus /System/Poweroff/Hibernate).

Thanks! Greetings.

---

### Post by scrooge_74 on 2007-10-30
A Fix depends on what version are you using, but this links could provide some help

[http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto](http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto)
[http://www.ubuntuforums.org/showthread.php?t=321369](http://www.ubuntuforums.org/showthread.php?t=321369)

---

### Post by gaiterin on 2007-10-30
My BIOS and motherboard isn't old.
I use Ubuntu 7.10.
With Windows Vista works the hibernate perfect.

---

### Post by scrooge_74 on 2007-10-30
I meant your version of Ubuntu, not the age of the BIOS or motherboard.  The same applies for hibernation with Vista or XP.  If something works with an MS OS that does not implies it works right out of the box in Linux.  you may have to tweak things before they work for you.

---

### Post by dz0 on 2007-11-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/135548](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/135548) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				this problem is reported (with some solution proposals) in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/135548")

---

### Post by gaiterin on 2007-11-04
Hi. Thanks by reply.
I think is the same bug :O

---

