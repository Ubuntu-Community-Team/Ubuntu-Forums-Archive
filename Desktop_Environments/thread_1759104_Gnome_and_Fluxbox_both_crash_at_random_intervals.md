---
title: "Gnome and Fluxbox both crash at random intervals"
date: 2011-05-15
forum: Desktop Environments
---

### Post by baseball116 on 2011-05-15
I just recently upgraded to Natty and I'm having a fairly annoying issue with Gnome and Fluxbox. There will be random intervals where I'll hit the enter key and my desktop environment will just quit out without any warning.

Now this is becoming a huge nuisance because I use time tracking software for work and I essentially lose time because once the environment crashes, the time is not saved.

Any help would be appreciated! I can provide logs as well if someone can tell me which ones they need.

I have dual monitors and I'm running the 64-bit version if it helps.

---

### Post by baseball116 on 2011-05-19
Anyone? Even after some updates it has been happening and it's really starting to affect my work :\

---

### Post by Krytarik on 2011-05-19
After that happened the next time, check the files "~/.xsession-errors.old" and "/var/log/Xorg.0.log.old" for related error messages.

Greetings.

---

### Post by baseball116 on 2011-05-20
Just happened again. Here is the log: [http://pastebin.com/bsGznLr5]("http://pastebin.com/bsGznLr5")

---

### Post by Krytarik on 2011-05-20
> **baseball116 said:**
> Here is the log: [http://pastebin.com/bsGznLr5](http://pastebin.com/bsGznLr5)
Was that really all?
It doesn't seem to be complete.

Also, what session option was that, Gnome or Fluxbox?

---

### Post by baseball116 on 2011-05-23
Sorry, must have accidentally not copied the entire log :\ When it happens again, I'll make sure to post the whole log. Also, that was in Gnome w/o Unity.

---

### Post by baseball116 on 2011-05-24
Just happened again, here is the full log: [http://pastebin.com/mYMAmMzi](http://pastebin.com/mYMAmMzi)

Again, it was on Gnome w/o Unity

---

### Post by Krytarik on 2011-05-24
The log doesn't give any definitive hint, but the repeated error messages in the lower part, right before the session crashed, are pointing towards Compiz.

Although it's not very widespread, there is a recurring issue with pressing the Enter key triggering an Xserver crash.

If possible, please use "Ubuntu Classic (No effects)" for a while, thus without Compiz running, to check if it's indeed responsible.

Also, what video card/chip do you have, and what driver are you running?

Maybe another video driver will fix the issue.

---

### Post by baseball116 on 2011-05-25
I have an nVidia GTX 470 and I'm using the most current version of the NVIDIA driver version 270.41.06

---

### Post by Krytarik on 2011-05-25
> **baseball116 said:**
> I have an nVidia GTX 470 and I'm using the most current version of the NVIDIA driver version 270.41.06
You may try the "nvidia-173" instead, as quite a number of users seem to have issues with the "nvidia-current" of Natty currently, whereas the 173 fixes their issues.

You may do the "No effects" test first.

---

### Post by baseball116 on 2011-05-25
No effects mode seems to be working but I'm installing the nvidia-173 package as I type this. Thanks for the help! :)

---

### Post by baseball116 on 2011-05-25
Still crashes with the enter button with "No effect" and I installed the nvidia-173 drivers and my Xsession wouldn't start up because my chipset wasn't supported so I had to revert back to the latest :/

---

### Post by Krytarik on 2011-05-25
Try the 3D-capable version of the "nouveau" driver, quite a lot users seem to have success with those.

It may be listed as "experimental" in "Additional Drivers". If it isn't, you can install it manually:
```
sudo apt-get install libgl1-mesa-dri-experimental
```

---

