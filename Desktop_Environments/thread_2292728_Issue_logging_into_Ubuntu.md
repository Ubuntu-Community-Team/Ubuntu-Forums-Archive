---
title: "Issue logging into Ubuntu"
date: 2015-08-30
forum: Desktop Environments
---

### Post by AtomicPenguin on 2015-08-30
I can no longer log into my Ubuntu Desktop. The guest account goes in fine. 

When I try to log into my user account the screen blanks for a second and then goes right back to the login prompt. 

Under the guest account it shows that it's using a 'built in display'  but this is a desktop pc. The native resolution for my monitor isn't shown as well. 

Any ideas?

---

### Post by AtomicPenguin on 2015-08-30
Had 3 files including xauthority owned by root. Made the changes listed above but it's still doing the same thing. Is there a way to drop both video card and monitor config in Unity to their defaults?

---

### Post by steeldriver on 2015-08-30
It's been a while since I've played with this kind of thing, but does your account have a ~/.config/monitors.xml file? if so, you might want to try moving or renaming it

---

### Post by AtomicPenguin on 2015-08-30
Removing it didn't help.

---

### Post by AtomicPenguin on 2015-08-30
Well something is mucked up as the guest account can't log in. I was following a guide on getting d3 to run with playonlinux and I must have screwed something up with the video drivers.

I can tell from the display resolution that is being used that I'm not using the Nvidia drivers anymore.

---

### Post by CantankRus on 2015-08-31
Link to the guide to give an idea of what you did.

---

### Post by AtomicPenguin on 2015-08-31
It's this one here. I mistakenly followed the bits about bumblebee and primus and I'm pretty sure that's where I destroyed things... 

[http://askubuntu.com/questions/440213/how-to-play-diablo-iii-on-ubuntu](http://askubuntu.com/questions/440213/how-to-play-diablo-iii-on-ubuntu)

---

### Post by AtomicPenguin on 2015-08-31
I fixed it by running....


```
sudo apt-get purge nvidia* bumblebee
```

---

