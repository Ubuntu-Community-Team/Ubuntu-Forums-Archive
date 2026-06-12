---
title: "Windows giving better battery life"
date: 2009-05-29
forum: General Help
---

### Post by sgtbug on 2009-05-29
Hi guys

I am using an ASUS EEE PC 1000HE. It came pre-installed with the dated XP Home. As soon as I got it, I installed UNR on it using my SD card.

The battery performance in Windows is a a lot better than that on UNR. I have even installed EEE-Control and tried the power save mode, turned off wifi, bt, card reader, cam.

Does anyone know how to solve this problem?

Please help, I don't wanna be stuck with Windows.

---

### Post by Bachstelze on 2009-05-29
Edited unnecessarily rude thread title.

---

### Post by sgtbug on 2009-05-29
lol.. sorry for that.. some help pls..

---

### Post by sgtbug on 2009-06-24
still no help? I'm getting about 6.5hrs of video playback in windows and only 4.5hrs in ubuntu.. i am pretty sure something isnt right..

---

### Post by hibliss on 2009-06-24
The battery life just is not as good in Ubuntu, but I definitely get more than 4.5 hours. Where is your screen brightness set?

You will just need to realize that Windows came preinstalled and Asus optimized the machine for windows with a utility they designed. It is still a relatively new machine, so it will not have identical performance to Windows in every aspect.

---

### Post by 3rdalbum on 2009-06-24
Have you tried using Intel Powertop to see what is using your battery power?

When you launch Powertop (sudo powertop), it will give you a couple of suggestions of things that it can change for you, to improve battery life.

After doing those, you might find that the "kernel" might be causing a large number of wakeups-per-second. Sometimes it will list specific kernel modules that are causing that battery drain. If so, you can usually:

```
sudo modprobe -r modulename
```

where modulename is the name of the kernel module you want to temporarily remove.

Removing a hundred wakeups-per-second is possible, especially if you use the suggestions on [www.linuxpowertop.com](www.linuxpowertop.com). This should yield more battery life.

Once you know your computer can run without the power-draining modules, you can add them to /etc/modprobe.d/blacklist.conf so they will never load.

---

### Post by hibliss on 2009-06-24
Thank you so much! I just installed powertop through Synaptic and and checking now to see if I can improve my battery performance.

---

### Post by philcamlin on 2009-06-24
ubuntu should be getting better battery like then windows...

yes using that command above should help :popcorn:

have fun

---

### Post by blueridgedog on 2009-06-24
The powertop link appears to be a dead domain.  Try this one:

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by hibliss on 2009-06-24
It is in the Jaunty repo.

---

### Post by sgtbug on 2009-07-07
u can do that using that eee tray icon too.. but even then.. windows i manage abt 6-7hrs of video playback.. ubuntu only 5 hrs or so..

i think the hdd usage is very high in ubuntu.. hav any of u faced performance lapses during a data transfer on the hdd?

---

### Post by hibliss on 2009-07-07
I hear my fan spinning more and faster in Ubuntu than in Windows as well.

---

### Post by nielsek on 2009-07-07
same here. i use eee 1000h with that eee-control-tray

---

