---
title: "Kernel Updates and Grub"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Tarvok on 2006-07-18
Background: I am currently dual-booting between Windows XP and Dapper Drake from a computer not my own. I take this liberty since I am the de-facto tech support for the house (whether I am living here or not), so it's okay... so long as my parents NEVER notice that it is there. (They are aware, but my father in particular doesn't want anything... different... happening when he turns it on.) That means Windows XP must boot by default, with minimal time for Grub's menu. To this end, I set up menu.lst with Windows at the top of the list and a two-second delay. When I want to boot into Ubuntu, I just hit "down" first chance I get to get through the menu before my two seconds is up.

Problem: Every time there is a kernel update, menu.lst is overwritten, wiping Windows out of the file. I generally forget that it does this, and next thing I know, my father is giving birth to a cow.

I know, I know, I could just skip the kernal updates, or just remember... but it seems a little wrong that updating screws up something as simple as menu.lst. Is there anything I can put in that file to signal to the updater not to touch the windows entry?

---

### Post by arjaybe on 2006-07-19
I've been noticing this. too.  Every time the kernel upgrades, my menu gets altered, and not in a nice way.  I would really like to keep my menu as is, and simply edit it for the new kernel.

---

### Post by routerstu on 2006-07-19
the only clean way i have seen to deal with this is to remove unused kernels in synaptic.  there may be easier ways but this does work.  this has been covered in the forums.  i am interested in any alternative solutions.

:)

---

### Post by arjaybe on 2006-07-20
That's a problem for me because I have several distros using a common /boot directory and the menu.lst ends up with several entries for each one.  They're all called Ubuntu and all assigned hda1.

My workaround is to back up menu.lst, upgrade the kernel and copy menu.lst back.  Today's Kubuntu kernel upgrade didn't need an edit of menu.lst, but version upgrades do.

A related problem is the schmozzle resulting from a fresh install.  I hope Ubuntu learns to play well soon.  Or maybe it's GRUB?

---

### Post by philippe_carlo on 2006-07-20
> **arjaybe said:**
> That's a problem for me because I have several distros using a common /boot directory and the menu.lst ends up with several entries for each one.  They're all called Ubuntu and all assigned hda1.

My workaround is to back up menu.lst, upgrade the kernel and copy menu.lst back.  Today's Kubuntu kernel upgrade didn't need an edit of menu.lst, but version upgrades do.

A related problem is the schmozzle resulting from a fresh install.  I hope Ubuntu learns to play well soon.  Or maybe it's GRUB?

There are two easy steps to prevent this from happening:
(1) Do not install kernels or kernel-related packages with their explicit version numbers, but use the meta package linux-386 or linux-686. In this way, old kernels get removed from the grub list upon updates, and grub stays clean.
(2) Add extra non-ubuntu entries BELOW the line saying
```

### END DEBIAN AUTOMAGIC KERNELS LIST

```

doing this, I have no such problems here. My grub stays clean, no matter what updates.

---

### Post by arjaybe on 2006-07-20
> **philippe_carlo said:**
> There are two easy steps to prevent this from happening:
(1) Do not install kernels or kernel-related packages with their explicit version numbers, but use the meta package linux-386 or linux-686. In this way, old kernels get removed from the grub list upon updates, and grub stays clean.
(2) Add extra non-ubuntu entries BELOW the line saying
```

### END DEBIAN AUTOMAGIC KERNELS LIST

```

doing this, I have no such problems here. My grub stays clean, no matter what updates.

Thank you.
(1) I don't think this would work with standard upgrades, as they supply a specific kernel package.  While my Kubuntu upgrade replaced a kernel package with the same name, so there was no edit of menu.lst necessary, it still wrote a new menu.lst with eighteen incorrect entries above the "### END DEBIAN AUTOMAGIC KERNELS LIST" line.
(2)  It did leave four of the original five entries below that line, but deleted the one for the distro in hda1, leaving the old Kubuntu entry at hda3.

Your fix no doubt works in a singular /boot, but I don't think it applies to a shared /boot.

---

### Post by Steveire on 2006-07-20
Ah, thanks. I reckon that'll help me out. I don't see any problem with a shared boot partition either. Where do you get that idea? Do you have other non-debian distros changing the file too?

The only issue I see with this now is that you don't have as much control over what order you put your grub entries in. So I still think the automagic grub menu thing needs to change.

In fact, I'm not even sure it would solve the OPs issue to put the entry below that line. Is there an upper line too?

Regarding the OPs other issue, you can make it so that the grub menu doesn't show at all unless you press ESC. Check the grub docs.

---

### Post by arjaybe on 2006-07-20
> **Steveire said:**
> Ah, thanks. I reckon that'll help me out. I don't see any problem with a shared boot partition either. Where do you get that idea? Do you have other non-debian distros changing the file too?

The only issue I see with this now is that you don't have as much control over what order you put your grub entries in. So I still think the automagic grub menu thing needs to change.

In fact, I'm not even sure it would solve the OPs issue to put the entry below that line. Is there an upper line too?

Regarding the OPs other issue, you can make it so that the grub menu doesn't show at all unless you press ESC. Check the grub docs.

Having a shared /boot partition means there are many other kernels in there besides the one for the distro in use.  The upgrade makes incorrect entries for all of them.

In addition, it removes one of the supposedly untouchable entries below the "Automagic Kernel" line.  It might be assuming that the entry in hda1 belongs to it, but if it's another distro (or Windows for those of that persuasion.-) then it's a problem.

If the OP's father's computer has Windows at hda1, then I don't think putting it below the "Automagic" line will help.

---

