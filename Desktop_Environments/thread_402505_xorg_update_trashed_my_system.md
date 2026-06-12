---
title: "xorg update trashed my system"
date: 2007-04-05
forum: Desktop Environments
---

### Post by raffytaffy on 2007-04-05
im very upset. this isnt the first time an xserver updtate hoed my stem. this time its bad. whenever i try to start any opengl app my xserer restartss and imback at the login screen. i found a solution on launchpad to reinstall mvidia driver. easier said then done. i have custom kernel.. i have to go into console to stop gdm and install that way...CANT DO THAT. i press ctrl alt + f1.. the screen turns black and xserver restats. im getting very tiered of these updates constanly breaking an otherwise stable system. if i fixd this im never updating again.

---

### Post by phidia on 2007-04-05
Are you trying to stop gdm by doing > sudo /etc/init.d/gdm stop?
If that doesn't work then do > sudo init 1
That should end the xsession.

---

### Post by kidders on 2007-04-05
Hi there,

If you're using a custom kernel, you should be cautious when installing updates.

In any case, the latest nvidia restricted driver is having some problems (it appears as though Ubuntu's version of it is missing a few things). Assuming you're using it, try downgrading to the last version that worked for you.

---

### Post by raffytaffy on 2007-04-05
yes ..i would do as suggested...only i cant go into a console using ctrl + alt+f1 . console login dosent work either. so i cant install nvidia driver.  so i dont know what to do.

---

### Post by phidia on 2007-04-05
I assume you've tried the other function keys too? i.e F2-F9
If you can't get to CLI normally you can boot the livecd and mount and chroot into your install.

---

### Post by kidders on 2007-04-05
You sometimes need to be a little patient switching local terminals ... CTRL+ALT+F1 can take a moment (or a couple of tries) on occasion. Starting or stopping your display manager will also cause some automated bouncing around between terminals.

Try booting your PC, waiting for the blue dialog box of death to pop up, and *then* switching terminal. Alternatively, an SSH server + another computer would be nice and easy ... you could go straight to phidia's instructions.

(**Edit: ** LiveCD! Now why didn't I think of that?! That'd work!)

Any help?

---

### Post by raffytaffy on 2007-04-05
gedited my xorg . changed 'nvidia' to'nv' , somehow loged into console, reinstallednvidia driver. now it works. still worried about future updates thou:(

---

### Post by phidia on 2007-04-05
Glad you got it working. Updates can be hell-what's that old adage?
"If it ain't broke don't fix it."

---

### Post by cmost on 2007-04-05
This is an easy fix; there have already been several posts about the problem.  The xorg update replaces a key file that the nvidia driver needs (especially if you're running compiz or beryl.)  You will simply need to reinstall the nvida driver to solve the problem.

---

### Post by kidders on 2007-04-05
Yep... This isn't the first time nvidia drivers have caused trouble either! (Not that I need to tell *you* that!) My tendency is to wait a while after a new release, and if nobody moans about it, *then* it might be worth installing.

At the moment however, I'm using the driver direct from nvidia's website, which comes with its own set of problems! I'm expecting the system updates I'm installing right now to break it, so I'll have to compile it again.

In my opinion, you really shouldn't update restricted graphics drivers unless the upgrade fixes a bug you have experienced, or introduces a new feature that you actually want. (**Edit:** ie what phidia said hehe.)

---

