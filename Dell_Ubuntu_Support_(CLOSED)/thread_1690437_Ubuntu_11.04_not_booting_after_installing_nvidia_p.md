---
title: "Ubuntu 11.04 not booting after installing nvidia proprietary drivers"
date: 2011-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by smithcl on 2011-02-18
Hi,

I have a dell latitude d830 with a  NVIDIA Quadro NVS graphics card.
I just upgraded to 11.04 from 10.10. I then updated my nvidia drivers. now when i reboot it freezes at the ubuntu logo at startup. Pressing Esc or alt F1 or ctrl alt F1 does nothing (tried various combinations and nothing happens). So i have no option to boot into Recovery mode or anything like that.
ALl i have is a usb stick which i can boot off Ubuntu 10.10 with. I can access the file system of the ubuntu install from this, is there anything i can change? I cant see any xorg.conf files as suggested in other posts. I dont want to try a reinstall, want to see if i can actually sort it.
im a windows guy trying to make the crossover and so far i'm liking it, so i want to keep giving it a go, so assume i have next to zero knowledge about linux.

thanks

C

---

### Post by mifth on 2011-02-19
Hi! I have the same problem with kubuntu 11.04 Alpha 2 after upgrading nvidia driver. My video card is gts 250.

---

### Post by ninjaaron on 2011-02-20
You will probably get more help at the Natty Narwahl Testing and Discussion board. All I can tell you is this: Don't expect much from an OS in alpha. If you are just coming over from windows, stick with 10.04 until the end of April (in fact, it's often better to wait a month or two after release for the upgrade for all the bugs to really be worked out).

---

### Post by C.C.C.P. on 2011-04-30
Looks like I got the similar problem, but in my case I updated two days ago, when Ubuntu 11.04 was released here is the screenshot of the the error message. I could boot in to safe graphics mode, but when I login into new Ubuntu 11.04 I can see desktop, but cant see start menu, also Alt+F2 not working, shortcuts to terminal are also not working. I got an NVIDIA 9700m, and used 16:10 1680*1050 resolution before, didnt have any problems during upgrade to 10.10 from 10.04 and others, this is the first time I see this problem! Is it related with GNOME, or new kernel?

[ATTACH]190553[/ATTACH]

---

### Post by Novacaptain on 2011-05-01
do you actually get to the log-in screen? 

If you select your user name (so that the password prompt appears) you can choose, at the very bottom of the screen, to start in classic mode (skipping unity).  

Does that work any better?

As far as i know, unity requires Compiz, which requires OpenGL. There might be something wrong with either of these. There is a tool for configuring openGL under system settings/compiz manager, perhaps try using a minimal set of features there?

---

### Post by f1ier on 2011-05-01
Try adding memory at start-up time (vmalloc) - I answered this in another thread... here's the howto:

[http://www.warp1337.com/content/ubuntu-1104-natty-segmentation-fault-nvidia-geforce-9-series-kernel-failure-solved](http://www.warp1337.com/content/ubuntu-1104-natty-segmentation-fault-nvidia-geforce-9-series-kernel-failure-solved)

---

