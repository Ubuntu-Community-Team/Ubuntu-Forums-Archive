---
title: "no mouse cursor in Gnome"
date: 2010-03-04
forum: Desktop Environments
---

### Post by RasterBurn on 2010-03-04
hello, i am not sure if anyone has had the same problem as i am having but um... I am running Ubuntu 9.10 x86_64 on my computer, earlier today i got the updates for cups and kernel image anyways, when i boot into the new kernel image (2.6.31.20.33) the mouse is fully functional but i dont have a cursor to tell me where the hell i am on the screen with my mouse, all the previous kernel images work fine for me so i am forced to continue using version 2.6.31.19 instead of 2.6.31.20 has anyone else encountered the same problem?

---

### Post by xarhelios on 2010-03-04
Sounds like an issue in your Xorg, do you have the hal and fam/gamin daemons installed?

---

### Post by RasterBurn on 2010-03-04
I have hal and gamin installed i believe they are part of the installation process through the live disk

---

### Post by xarhelios on 2010-03-04
With hal and gamin, you may not even need a xorg.conf. Try backing up and deleting it then reboot and see what happens. 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm /etc/X11/xorg.conf
```

---

### Post by yoi on 2010-03-06
Hi there,

My case seems somewhat similar:
Whenever I change the screen resolution by xrandr command, the refreshed screen loses a mouse pointer.  To get the missing mouse pointer back, I always move into a virtual console by Ctrl + Alt + F1, then back to the X session by Ctrl + Alt + F7.  Mysteriously, this brings back my mouse pointer.

I am not sure this applies to your case, but it should be a quick test.  It might work.

---

### Post by RasterBurn on 2010-03-06
ok just got around to dealing with the new kernel-image problem, got my machine running properly with the new kernel (i guess its time to fix the less important problems) anyways the way it was working out for me, boot into the new kernel -> lost mouse pointer, so i booted into the prev. one and deleted the xorg.conf file, booted back into the new one to find my xorg settings are back to live intstall :( and then i reinstalled the graphics driver for my sapphire hd 3870 cards and now its good to go :D

---

### Post by Esperens on 2010-03-11
Thanks for the info how to remove xorg.conf. It helped me alot. But the ATI driver where lost. I tried to reinstall it but then the problem come back. Ubuntu is new to me, so could someone please explain more specific, like xarhelios, how to install ATI driver if it's not like the ordinary way. Like 

sudo sh ./ati..................run

And btw isn't this problem a bug in Ubuntu 2.6.31.20 or is the ATI driver buggy?

---

### Post by sdaau on 2010-05-04
Hi yoi,

> **yoi said:**
> To get the missing mouse pointer back, I always move into a virtual console by Ctrl + Alt + F1, then back to the X session by Ctrl + Alt + F7.  Mysteriously, this brings back my mouse pointer.

I am not sure this applies to your case, but it should be a quick test.  It might work.

Thanks, that worked for me - 10.04, 32 bit (I believe my missing pointer may have to do with Synergy running while leaving the PC to go to suspend).

Thanks,
Cheers!

---

### Post by koalabk on 2010-05-07
I have installed the 64bit version of karmic koala, on a barebones box.
I installed the desktop version.
I managed to ctrl-alt-F1 occasionally,
but every time I move my mouse to the menu bar, it freezes up;
then I try ctrl-alt-F1, and find that the Keyboard also is frozen.
This is a real headache.
Anyone know if the latest LTS version might have fixed these bugs ?
btw, for the record, I have no Xorg.conf.

So, no keyboard, no mouse; maybe soon no koala, or no ubuntu.
Any ideas would be appreciated :)

---

