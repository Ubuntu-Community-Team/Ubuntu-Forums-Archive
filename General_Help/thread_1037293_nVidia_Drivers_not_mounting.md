---
title: "nVidia Drivers not mounting"
date: 2009-01-11
forum: General Help
---

### Post by pinksoviet on 2009-01-11
Hi, I currently run Intrepid Ibex on a Thinkpad T61p, and it's actually been quite the pleasant experience. However, after I installed three "critical updates" two days ago, my nVidia kernel is apparently not being mounted due to an error, so I end up having run in low graphics mode the entire time. Everything else works perfectly fine, however.

I tried using EnvyNG, but it gives me an error saying that I don't have the headers installed. So I checked and they are indeed installed (the latest ones). So I suppose it would be nice if some of ya'll could help me figure out this problem so I can use the nVidia drivers and return to a more comfortable resolution.

---

### Post by gettinoriginal on 2009-01-11
Sometimes during an update the "hardware drivers" get disabled.  Check under system, admin, hardware drivers to make sure it is enabled.  :p

---

### Post by pinksoviet on 2009-01-13
The proper hardware driver is enabled, but before Ubuntu finishes booting, it gives me an error dialog box that says that the nVidia kernel has failed to load or something to that effect.

---

### Post by gettinoriginal on 2009-01-13
Just curious, do you have "ubuntu-restricted-extras" installed ??  It can be found in Synaptic.  :p

---

### Post by pinksoviet on 2009-01-14
I just installed the ubuntu-restricted-extras after reading your post. Still, it does nothing discernable (to me, at least). If you'd like, I saved the error logs along with my current xorg.conf file. Would seeing them be helpful to diagnose the problem? Again, thank you.

---

### Post by gettinoriginal on 2009-01-15
yes, would like to see your output of those.

---

### Post by pinksoviet on 2009-01-15
Here they are. Thank you!

---

### Post by gettinoriginal on 2009-01-16
Make sure your Software Sources look like mine:
[ATTACH]100013[/ATTACH][ATTACH]100014[/ATTACH]

Then please run this in terminal:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by pinksoviet on 2009-01-16
I made sure my sources looked just like yours and I ran that line as you specified. Apparently nothing was updated or anything.

---

### Post by orlox on 2009-01-16
Ive had issues with the nvidia packages very frequently with updates. My solution, open synaptic, uninstall the drivers (mine is listed as nvidia-glx-177) and then reinstall it. Directly reinstalling didnt work for me...[I believe t was like this, hadnt had this problem in quite a while so I hope im remembering it right!]

Also, under system->administration->hardware controllers you should be able to change the version of the driver youre using, wich might help...

---

### Post by orlox on 2009-01-16
Erased the post because I forgot a small important detail! Never mind!

---

### Post by pinksoviet on 2009-01-17
Eek, that didn't work either.

---

