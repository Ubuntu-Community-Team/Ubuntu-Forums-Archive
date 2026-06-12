---
title: "Karmic freezes at start-up"
date: 2009-12-13
forum: Desktop Environments
---

### Post by Kermit524 on 2009-12-13
Hi,
I have already spent half a weekend on this - but still no clue.

Every morning, at first, sometimes even second boot, the system hangs.

Only thing on the screen is the Kubuntu start-up progress bar. 
Trying to use any key combination to halt, reboot, or switch terminal - get me nowhere. Everything is locked. Only way out - is hard shutdown - using the actual on/off button.

Next boot is normally ok.

When booting from livecd, or selecting recovery mode in grub - all's ok.

Ran couple of MEMTEST cicles - all looks fine. Also Ran a manual fsck. No alerts.

The computer is brand new, Intel I7, 6 GB ram. I am really at a  loss here, what else can I check? I realize this can also be caused by a hardware failure. How can I check exactly which part?

Is there a way to get rid of the Kubuntu start-up progress bar, and see at what stage exactly does the system hang? 

Many questions, no answer, real bummer...:-( Your help is greatly appreciated.

Many thanks in advance, and happy Hannukah/Christmas

---

### Post by Zorael on 2009-12-13
Well, you should be able to hit Ctrl+Alt+F1 when the splash shows to see the textual boot.

Alternatively, edit the grub entry for the kernel you're booting (by hitting E? I think), scroll down to the **linux** line, remove **splash** from it and hit Ctrl+X.

If you want a really, really verbose boot, do the same as above but also remove **quiet** from the same line.

The entry won't be saved to disk; it will merely be for that particular boot. So you can't break anything, really, since it will all restore itself at next boot.

---

### Post by Kermit524 on 2009-12-13
> **Zorael said:**
> Well, you should be able to hit Ctrl+Alt+F1 when the splash shows to see the textual boot.

Alternatively, edit the grub entry for the kernel you're booting (by hitting E? I think), scroll down to the **linux** line, remove **splash** from it and hit Ctrl+X.

If you want a really, really verbose boot, do the same as above but also remove **quiet** from the same line.

The entry won't be saved to disk; it will merely be for that particular boot. So you can't break anything, really, since it will all restore itself at next boot.

Thanks! I have edited the grub entry as you have recommended - and of-course, due to Murphy'es law, now the system booted with no problem... So I will try again tomorrow at first boot and see what I come up with.

Re switching to textual boot - that's one of the main issues here: When this happen, the keyboard is locked - and won't react to any key strike, thus I can't switch to a non graphic terminal and see what's going on.

---

### Post by Zorael on 2009-12-13
> **Kermit524 said:**
> Re switching to textual boot - that's one of the main issues here: When this happen, the keyboard is locked - and won't react to any key strike, thus I can't switch to a non graphic terminal and see what's going on.

You may be able to preempt the lockup and switch to the textual boot before time, but obviously, a modified grub entry does the same job easier.

---

### Post by Kermit524 on 2009-12-14
> **Zorael said:**
> You may be able to preempt the lockup and switch to the textual boot before time, but obviously, a modified grub entry does the same job easier.
You are right, of-course... I didn't think about that :-D

Here's an update: this morning - the system booted smoothly again. This is a first since this problem has started couple of days ago. Only thing I did was removing the silent splash.

So at the moment I can think of 3 things:
1. Murphy's law
2. Hardware failure that occurs only when the device is not yet warmed-up. Dealing with the grub menu gives it a suffice delay to warm up and get going.
3. The problem is ... within the xsplash itself! - this is the most improbable one as far as I am concerned.

Thanks again for your help sorting this out, andgreat day,

Michal

---

### Post by Kermit524 on 2009-12-14
...and yet another thing:
Is there a way to permanently remove the "fireworks" from start-up?
I would rather have a not-so-silent boot - i.e - saving those settings within the grub, so I don't have to edit the right kernel  each time anew?

Many thanks again, and in advance,

Michal

---

### Post by Zorael on 2009-12-15
It's not as easy as it used to be now that GRUB 2 is being used by default. Search these forums for GRUB 2 configuration guides; I know I've seen a few around. You want to change the command line variables (GRUB_CMDLINE*) being used in **/etc/grub.d/10_linux**, but I don't know where the proper place to do that is.

---

### Post by Kermit524 on 2009-12-15
> **Zorael said:**
> It's not as easy as it used to be now that GRUB 2 is being used by default. Search these forums for GRUB 2 configuration guides; I know I've seen a few around. You want to change the command line variables (GRUB_CMDLINE*) being used in **/etc/grub.d/10_linux**, but I don't know where the proper place to do that is.
Since My system is upgraded from Jaunty, and not installed from scratch, it still uses Grub1. Could you please advice how it is done on Grub1?
Thanks again in advance,
Michal

---

### Post by Zorael on 2009-12-16
You could either install **startupmanager** (among others) and change it graphically, or edit the **/boot/grub/menu.lst** file and find this section.
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=*<something>* ro quiet [COLOR="Red"]**splash**[/COLOR]
```
Delete [COLOR="Red"]**splash**[/COLOR] (and **quiet** if you want to), then do the following in a terminal.
```
$ sudo update-grub
```
Then it should update all your kernel entries with the default options you specified there.

---

### Post by Kermit524 on 2009-12-16
> **Zorael said:**
> You could either install **startupmanager** (among others) and change it graphically, or edit the **/boot/grub/menu.lst** file and find this section.
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=*<something>* ro quiet [COLOR="Red"]**splash**[/COLOR]
```
Delete [COLOR="Red"]**splash**[/COLOR] (and **quiet** if you want to), then do the following in a terminal.
```
$ sudo update-grub
```
Then it should update all your kernel entries with the default options you specified there.

Thanks again!

---

