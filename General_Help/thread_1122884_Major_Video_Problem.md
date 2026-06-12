---
title: "Major Video Problem"
date: 2009-04-11
forum: General Help
---

### Post by firewarrior on 2009-04-11
First I want to say I wasn't exactly sure where to post this. Sorry in advance.

I was playing Black and White 2 through Wine today and something major cliched with my video. I closed out the game in Wine, the background and the entire desktop environment went very very light and became very pixilated. I shut the computer down. Started it back up and now I can not get the resolution above 640x480 when i was at a 1280x1024. I've tried everything I can to fix this problem. I've tried going into the screen resolution options, tried to detect the video card, and tried to restart a couple of times and nothing seems to work. Please if there is anything that can be done to help it would be very very appreciated.

---

### Post by schmidtbag on 2009-04-11
What is your video card?

I've encountered similar issues to this, usually what works for me is just starting up the game again and then shutting it down.  when that doesn't work changing the resolution tends to help but apparently it isn't for you, which is why i need to know your video card.  you should try reisntalling it, or if not, run the settings that come with it (like the nvidia control center or ati catalyst)

---

### Post by firewarrior on 2009-04-12
The card that I have for my computer is a nVidia Geforce 8600 GT 512 MB PCI Express.

---

### Post by schmidtbag on 2009-04-12
well first, try reinstalling the nvidia drivers.  i heard about someone else who updated to the nvidia-glx-180 drivers and they got issues, so stick with 177.

if that doesn't work try restarting into recovery mode and select reset xorg or xserver, i forget which.  then reboot.

---

### Post by firewarrior on 2009-04-12
Ok something else happened again with the resolution settings. I was trying a couple of things and the resolution decided that it wanted to go to an even smaller setting. Something like 320x280, so now everything is so big that i can no longer see anything on the screen and cannot select anything. :( I'm thinking that I may have to reinstall ubuntu.

---

### Post by schmidtbag on 2009-04-12
did you try what i said?

---

### Post by firewarrior on 2009-04-12
i am not able to change the resolution so that i can see anything. that is why i'm thinking that i'm going to have to reinstall.

---

### Post by wfp on 2009-04-12
You could try booting into recovery mode then from the drop-down list choose repair X- Server. That should undo the last changes you made. Then once back to your desktop try enabling desktop effects again it should re-enable your driver again.

---

### Post by soltanis on 2009-04-12
Hit a virtual terminal and do

```

sudo dpkg-reconfigure xorg

```

---

### Post by firewarrior on 2009-04-13
thank you everyone for your help. :):):):):):):) I was able to get the xserver to fix the problem in recovery mode. thank you thank you thank you. i could kiss you all.

---

### Post by LouisZepher on 2009-04-13
I'm having the same problem.  

Intel integrated chipset.

I even reinstalled from an official copy of 8.10 and the problem remained even after upgrading to 9.04.

I should note, that when booting from the LiveCD, I had to choose "Safe Graphics Mode", otherwise I would see nothing other than my monitor's OSD message "VGA Mode not Supported".  (This used to flash for a moment during boot-up, but would otherwise enter a normal Gnome session with working graphics. {Other than the usual 3d acceleration issue that's existed for a while...})

I've tried [sudo dpkg-reconfigure xorg], and [Attempt to fix Xserver] during a recovery boot, and no-thing's working.

---

### Post by schmidtbag on 2009-04-13
what model is your integrated video?  or, at least how old is it?  I know someone who had an intel integrated video with 8mb and he couldn't get over 800x600.  i did get it over that at one point but i have no idea how.  all i can tell you is you will have to edit xorg

---

### Post by LouisZepher on 2009-04-13
> **schmidtbag said:**
> what model is your integrated video?  or, at least how old is it?  I know someone who had an intel integrated video with 8mb and he couldn't get over 800x600.  i did get it over that at one point but i have no idea how.  all i can tell you is you will have to edit xorg

Intel chipset, on (or rather *in*) a Gateway circa 2001 or so.

Thanks for replying, but just a few minutes ago, I found what the problem was:  Xorg was list my video card as "Vesa" rather than "Intel" - even after letting [dpkg-reconfigure xorg] do its thing.

Thanks again, and sorry that I didn't get around to editing my last post before you replied to it.):P

---

