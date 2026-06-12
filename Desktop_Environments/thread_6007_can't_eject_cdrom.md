---
title: "can't eject cdrom"
date: 2004-11-24
forum: Desktop Environments
---

### Post by tanari on 2004-11-24
after inserting CD I can't eject CD-ROM (eject button on my CDROM doesn't work). I must go to Computer>Disks> Right Click on CDROM icon and press eject.

---

### Post by arctic on 2004-11-24
which vendor is the cd-rom? does it happen will all cds or only some? which services are running?

---

### Post by jdong on 2004-11-24
That's normal. In Linux, you *must* unmount a volume before you can eject it -- for the sake of application stability.


Perhaps in the future HAL will have a workaround, but to me , this behavior is very desirable.

---

### Post by Jad on 2005-01-26
Having same problem and watching /var/log/messages gave me this 

Jan 26 17:00:06 ubuntu -- MARK --
Jan 26 17:07:47 ubuntu kernel: udf: registering filesystem
Jan 26 17:07:49 ubuntu kernel: cdrom: open failed.
Jan 26 17:07:49 ubuntu kernel: cdrom: open failed.
Jan 26 17:09:00 ubuntu last message repeated 8 times
Jan 26 17:12:54 ubuntu kernel: cdrom: open failed.

---

### Post by jdong on 2005-01-26
[QUOTE=jdong]That's normal. In Linux, you *must* unmount a volume before you can eject it -- for the sake of application stability.


Perhaps in the future HAL will have a workaround, but to me , this behavior is very desirable.[/QUOTE]

Once again, **YOU AREN'T SUPPOSED TO BE ABLE TO EJECT A CD** without unmounting first, either by the right-click +eject, **umount /dev/cdrom** at a console, or **eject /dev/cdrom**.

---

### Post by Totenglocke on 2008-04-26
See, if you're currently running something off the cd, then I completely understand why they would want to do that.  However, when the cd is just sitting in there and nothing is accessing it, it's a pointless hassle to not be able to just hit the eject button.

I just switched to Ubuntu from XP and other than this, I haven't found anything to complain about.

---

### Post by rnrover on 2008-05-02
> **Totenglocke said:**
> See, if you're currently running something off the cd, then I completely understand why they would want to do that.  However, when the cd is just sitting in there and nothing is accessing it, it's a pointless hassle to not be able to just hit the eject button.

I just switched to Ubuntu from XP and other than this, I haven't found anything to complain about.

I have Hardy on one machine and Gutsy on another one, and when I do not have a cd in the cup holder, I cannot use the eject option on the drive icon to open the drawer.  Why is that option in the menu if it doesn't work. I get a response of "Unable to Mount Media There is probably no media in the drive"

It makes me want to say no $hlt Sherlock. Open the drawer and I will put you some media in there.  You would think after two versions this bug could be fixed, or remove that option from the menu.

These are the Newbie things that make you give up.  I saw another post about creating an applet to run the eject command.  That is something you can't do in windows, however you don't have to because their eject command works every time.

I have posted another question about this issue two weeks ago and have not had a response that is a solution. Only workarounds. I believe it is related to permissions of the user, but I cannot find where to make that change.

---

