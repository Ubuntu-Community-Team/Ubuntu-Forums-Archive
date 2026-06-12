---
title: "XBox 360 Guitar Controller with Hardy"
date: 2008-05-30
forum: Gaming &amp; Leisure
---

### Post by GoblinInventor on 2008-05-30
Hello all,

I've been trying to get the x-plorer guitar controller to work with hardy, have followed every guide I can find, and whenever I try to do

```
modprobe xpad
```

it just hangs. By that I mean that it never finishes the task. If I try to start the computer with the guitar controller in it, it hangs as well. Any help would be much appreciated.

---

### Post by Boktai1000 on 2008-06-01
Ive got (had) the same problem, read my threads here mabe we can get some assistance.

[http://ubuntuforums.org/showthread.php?p=5095226](http://ubuntuforums.org/showthread.php?p=5095226)

[http://ubuntuforums.org/showthread.php?t=807040](http://ubuntuforums.org/showthread.php?t=807040)

My Guitar was working till I installed the 360 controller xpad following the "Official" guide on the Ubuntu wiki linked here [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) .  After installation,  If its plugged in Ubuntu will not boot with it plugged in, but my 360 controller works flawlessly.

---

### Post by werries on 2008-06-01
thats a known bug. dont plug it in until you boot.
im happy with my connected 4 xbox 360 controllers in and playing 4 player Goldeneye via Mupen64 with friends. =D

---

### Post by Boktai1000 on 2008-06-02
I just actually plugged my Guitar Hero Xplorer in after boot and did these commands.

sudo depmod -a
sudo modprobe xpad

and i went into Frets on Fire and tried to keybind something and it worked :guitar: im not gona complain now that its working but i hope one day this bug is fixed so others wont have to go through this same situation.

edit: btw unplugging and replugging the guitar back in while in the same session will make the guitar not work, but a simple reboot it seems fixs that.

---

