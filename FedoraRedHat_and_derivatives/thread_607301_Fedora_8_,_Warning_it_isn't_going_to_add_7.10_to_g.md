---
title: "Fedora 8 , Warning it isn't going to add 7.10 to grub."
date: 2007-11-08
forum: Fedora/RedHat and derivatives
---

### Post by Wiebelhaus on 2007-11-08
What in the world is up with an OS these days that can't auto detect other OS's and add them to grub?

It's just unacceptable.


So far , not so good , although I'll say the interface which allot of you 
won't see much difference from 7.10 is slick , ohh yea btw , YUM is busted on a fresh install - lol

---

### Post by wolfen69 on 2007-11-09
i run 4 OS's now, -ubuntu 7.04, kubuntu 7.10, suse 10.3, and xp (games only, network card disabled) and tried to add fedora 8. install went well, but after reboot, there was no sign that fedora did anything to grub. nothing. i even tried changing the boot order of the drives, but still nothing. it seems that fedora has a problem with grub. oh well, there's many other distros to try.

---

### Post by vexorian on 2007-11-09
I don't think any linux distribution's installer actually detects any other distribution or even older versions .

I think that there's barely windows support to help migration. Nobody really focuses on ubuntu's market share so adding support to dual boot it would be quite lame. This said, it is easy or at least possible to restore grub.

My generalization would be that once you install two different linux distros on the same computer without removing the previous one you are probably an advanced user already and can deal with setting up grub.

I would bet ubuntu does the same to Fedora.

---

### Post by wolfen69 on 2007-11-09
> **vexorian said:**
> ***I don't think any linux distribution's installer actually detects any other distribution or even older versions .***

I think that there's barely windows support to help migration. Nobody really focuses on ubuntu's market share so adding support to dual boot it would be quite lame. This said, it is easy or at least possible to restore grub.

My generalization would be that once you install two different linux distros on the same computer without removing the previous one you are probably an advanced user already and can deal with setting up grub.

I would bet ubuntu does the same to Fedora.

not quite true. ive installed several distros that had no problem seeing other distros.

---

### Post by Mithrilhall on 2007-11-09
> 
not quite true. ive installed several distros that had no problem seeing other distros.

I agree.

---

### Post by meho_r on 2007-11-09
Same here. openSUSE 10.3 recognized my Ubuntu and WinXP, as Ubuntu recognize openSUSE and WinXP. No problem at all.

---

### Post by 20thCenturyBoy on 2007-11-09
Fedora recognized Windows, Ubuntu, and Arch on my rig...?

Thats strange.

---

### Post by Wiebelhaus on 2007-11-10
> **20thCenturyBoy said:**
> Fedora recognized Windows, Ubuntu, and Arch on my rig...?

Thats strange.

yes it is.

---

### Post by eljoeb on 2007-11-10
Fedora 8 recognized my Vista and Ubuntu.  Bummer.  I was hoping to post some indignant comment and further the cause against the ghastly Fedora.  Oh wait.  Never mind.

I am still figuring out why I need two Linux distros on one computer, but that's a topic for another thread.

---

### Post by Caser on 2007-11-18
Hi guys
I have three HD, I installed winXp on the first hard disk then i installed Ubuntu gutsy on the second one,
grub automatically identified winxp and every thing is working good.
the third hard disk was for storage, i created i new empty partition on it 49GB and installed F8 on it...
but it only automatically added winxp and trashed ubuntu,
what i did is this :
copied the default entry  in  menu.lst from ubuntu and pasted it in menu.lst for 
Fedora 8
and now every thing is doing fine !!
 i found this in a post for Junior Hacker in linuxquestions.org

---

### Post by RebounD11 on 2007-11-20
Detected WinXP, and OpenSuSE 10.3 on my cousins computer.

---

