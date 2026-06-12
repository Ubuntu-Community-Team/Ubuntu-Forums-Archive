---
title: "Different grub version?"
date: 2009-05-29
forum: General Help
---

### Post by FlyingSaucrDude on 2009-05-29
I'm a recent Ubuntu convert (I used to run Fedora).  Anyway, I'm using grub (since I dual boot Windows as well), but I've noticed some differences between the version of grub that Ubuntu gave me and the version Fedora had.

In particular, in the version of grub I got with Fedora, the hiddenmenu command allowed you to press any key (not just escape) to access the menu.  It also displayed which option it was going to boot during the countdown.  (For an example, see [http://www.electrictoolbox.com/images/grub1.png](http://www.electrictoolbox.com/images/grub1.png))

In the Ubuntu version, though, the hiddenmenu command requires you to press the Escape key (and only the escape key) to access the menu, and it doesn't show which option it's going to boot.  (For an example, see my attachment.)

I really preferred the interface of the Fedora version, so I was just wondering -- is there a way to change it?  As far as I can tell, both versions claim to be GRUB v0.97, so I'm not completely convinced they're really different versions...maybe there's some sort of advanced configuration I'm missing that affects the behavior of the hiddenmenu command?  I've tried googling high and low for a solution, and can't seem to find one...

Does anyone have any ideas?

---

### Post by lindsay7 on 2009-05-29
Get "startup-manager" from Synaptic. You will then find it under System/administration. You will be able to change up the grub menu from there.

---

### Post by FlyingSaucrDude on 2009-05-29
> **lindsay7 said:**
> Get "startup-manager" from Synaptic. You will then find it under System/administration. You will be able to change up the grub menu from there.

First off, thanks for the suggestion!  Unfortunately, I've tried using just about every option in startup-manager, and none of them do what I've asked for.  (I should point out that I'm quite comfortable editing the grub menu.lst configuration file by hand too.)  With that said, if you know of a specific option in startup-manager I should use to enable pressing any key (and showing what entry is going to boot before entering the menu) then that would be great -- thanks!

For now though, startup-manager doesn't seem to be the solution.  :(

---

