---
title: "Dell XPS M1330: cannot switch to CRT"
date: 2008-02-20
forum: Dell  Ubuntu Support
---

### Post by bluemig on 2008-02-20
Hi,

I just received my M1330 with Ubuntu pre-installed :)

Taking the machine in hand, i switched the display to my (also brand new) acer 22" flat monitor using the Fn-F8. Great display !

I logged out, the display switches back to the laptop LCD. Why not.

But from now, whatever i do, relogin, cold reboot, this Fn-F8 does not work anymore. It just does nothing and the display remains on the laptop.

I can't believe this feature is supposed to work only once in the machine's life :(

An idea anyone ?

Thanks,
/mig

---

### Post by bluemig on 2008-02-20
Or maybe is there some command line trick to switch the display like i810switch that works on Acer laptops ?

---

### Post by bluemig on 2008-02-20
After searching around this, i now assume the Fn-F8 was really a once-only feature.

Ok, i'll forget about Fn-F8. I can now see things on my external monitor by tickling the xorg.conf

However, i'm having a hard time with setting things up there. 
Looking around, it seems that people are using the nvidia-settings and nvidia-xconfig (forgot to tell i have a nvidia geforce 8 on my m1330).

On my laptop, the installed nvidia programs are scripts that contain:

#!/bin/sh
#This script is a placeholder replacement for the "nvidia-xconfig" tool which has been intentionally removed from this system
exit 0

It took me one hour to figure out why calling those programs did not give much result (i would like to spend some time with the genius guy who wrote this script without doing "echo 'script has been removed''

Can someone either:

1- tell me where i can find a replacement for those nvidia programs or tell if and why i should not use them
2- post a working xorg.conf with maximum laptop resolution, ideally with a second monitor
3- point me to a working xorg.conf such as 2-

Thanks,
/mig

---

### Post by anaspeople on 2008-02-29
I bought my this laptop with vista (way cheaper) and erased it to install ubuntu with dell reinstallation iso.
I managed to switch screens only once but I cant anymore. Any idea? Please somebody help, I really need this feature!

---

### Post by ChaosParser on 2008-02-29
> **bluemig said:**
> Hi,

I just received my M1330 with Ubuntu pre-installed :)

Taking the machine in hand, i switched the display to my (also brand new) acer 22" flat monitor using the Fn-F8. Great display !

I logged out, the display switches back to the laptop LCD. Why not.

But from now, whatever i do, relogin, cold reboot, this Fn-F8 does not work anymore. It just does nothing and the display remains on the laptop.

I can't believe this feature is supposed to work only once in the machine's life :(

An idea anyone ?

Thanks,
/mig

You didn't switch back to the LCD with FN+F8 before you logged out.  Try creating a new user, doing the same thing you did before but then using FN + F8 to switch it back BEFORE you log out.

---

### Post by anaspeople on 2008-03-01
> **bluemig said:**
> After searching around this, i now assume the Fn-F8 was really a once-only feature.

Ok, i'll forget about Fn-F8. I can now see things on my external monitor by tickling the xorg.conf

However, i'm having a hard time with setting things up there. 
Looking around, it seems that people are using the nvidia-settings and nvidia-xconfig (forgot to tell i have a nvidia geforce 8 on my m1330).


Could you please post what you had to change in xorg.conf to make switching to a monitor posible again? Thanx.
I'm quite desperate about it.

---

### Post by anaspeople on 2008-03-02
I just wanted to use Fn+F8 but it it wouldn't work.
Anyway I've just found out nvidia-settings can do all I need.
I'm really happy about it.

---

