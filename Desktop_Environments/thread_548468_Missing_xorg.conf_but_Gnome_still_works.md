---
title: "Missing xorg.conf but Gnome still works"
date: 2007-09-11
forum: Desktop Environments
---

### Post by jeepescu on 2007-09-11
Something weird happened last night. 
After installing feisty and booting a number of times, at one moment, gnome refused to start. I got the text screen with the usual messages that the gdm could not be started. 
I have made absolutely no change in my config, I had no "good" xorg.conf to restore from. 
As I had nothing to loose, I renamed my existing xorg.conf and try to boot without one, see what gives.

Oh surprise, not only it started properly, but it also recognized my proper screen resolution (1920x1200), it was running in a max of 1024x768 before. My video card is an ATI x300. 

Now, is there a way to recreate xorg.conf without having to reinstall the whole shabang ? 
I remember seeing in a thread here some dpkg command that would do it, but I can't find it any more. 
I kind of need one now, as I want to make changes for the back-forward buttons for my mouse. 

Also, how come that now, I get the good resolution and before I couldn't? I did NOT install the ATI restricted driver, the box is positively unchecked.

Thanks in advance, 
BN

---

### Post by swisscow on 2007-09-11
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Is this the one you want?

Strange about xorg, wonder why..??

---

### Post by jeepescu on 2007-09-11
Gruezzi Milka und danke vielmal. 
This was the one I was looking for. 
I will try to run it tomorrow see what happens. 
BN

---

