---
title: "Vostro 1700 Wireless Not Working."
date: 2007-10-22
forum: Dell  Ubuntu Support
---

### Post by RangerDanger on 2007-10-22
I got a new Vostro 1700 and then waited two weeks for the release of 7.10 and installed it tonight.  Installed easier than 7.06 on my e1505, but the intel 3945 card will not connect to any networks, it can see them just not connect.  I have a sound and bluetooth problem but too, but I think I can figure them out later after the wireless.  Any ideas?

---

### Post by rock freak on 2007-10-22
wireless didn't work with me either but the problem for me at least seemed to be the kernel.  It didn't work in 2.6.22-14-386 kernel but booted into the generic 2.6.22-14-generic version and worked like a charm.  Hit esc to get into your grub menu and you can select it form there!!

Also having sound and bluetooth issues just about to look into them!!

Hope this helps

---

### Post by rock freak on 2007-10-23
Ok sound is sorted just in case you havn't found the thread yet it is [here]("http://ubuntuforums.org/showthread.php?p=3489580")

Thanks to Razzo!!

> **~chinook~ said:**
> the solution 

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Just about to look into the bluetooth issue but cant say i even had it working in fiesty but then again I forgot about it :D

---

### Post by RangerDanger on 2007-10-24
> **rock freak said:**
> wireless didn't work with me either but the problem for me at least seemed to be the kernel.  It didn't work in 2.6.22-14-386 kernel but booted into the generic 2.6.22-14-generic version and worked like a charm.  Hit esc to get into your grub menu and you can select it form there!!

Also having sound and bluetooth issues just about to look into them!!

Hope this helps

The only kernel I have is the 2.6.22-14-generic version I don't have a 386 kernel or any others.  I also can't figure how to update the kernel or add others to see if they work at all.  I have no way to get wireless working.

---

### Post by rock freak on 2007-11-02
Did you do it for a fresh install of gutsy by any chance?? Mine worked out the box one i had the right kernel!  But then again i upgraded from a relativly clean fiesty.

Still not had any joy with the bluetooth

---

### Post by djbon2112 on 2007-12-27
Sorry for a bump, but I'm having this problem, only it seems more serious.

I flick the switch on the side of the laptop on, but the WiFi light doesn't light up, and Ubuntu doesn't detect any wireless connections. I can't find drivers on Dell's site either. Anyone with any advice would be appreciated!

---

