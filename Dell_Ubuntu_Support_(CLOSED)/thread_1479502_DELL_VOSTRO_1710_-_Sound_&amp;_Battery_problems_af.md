---
title: "DELL VOSTRO 1710 - Sound &amp; Battery problems after upgrade to 10.04"
date: 2010-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mamahoo on 2010-05-10
Hi All,

Since my upgrade (Was running perfectly on 9.10) to 10.04 on my DELL VOSTRO 1710, I am facing the following "bugs" ???

1- When my laptop is connected to the power adapter and I disconnect it, I will systematically receive the following error:

[I][B]"The battery is critically low, your computer will soon shutdown"
[/B][/I]
Then, the following seconds, the laptop shutdown itself !! This happens whenever the battery is fully charged or not. :(

2- The sound module : 
**00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)**

doesn't work anymore since the upgrade to 10.04.
When I click on the ***sound preferences***, I get the following window for a few seconds:

[B]Waiting for the audio module ....
[/B]
than --> Nothing happens.

Have anyone face the same problem on same or other laptop brand?

Does someone have a bypass for the battery problem which is very anowing when moving the laptop from a power source to the other ;).

Thanks

O&O MamahoooOOooOOOo

---

### Post by Idefix82 on 2010-12-29
I can confirm problem 1. Since my graphics card also broke just two days after I installed 10.10 (I am sure that that's a coincidence), I haven't had any chance of investigating the problem any further.

---

### Post by lidex on 2011-01-05
Sounds like an acpi issue and probably a regression at that. Not my area of expertise. You could try a more recent kernel to see if that's the problem. Go here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
For the audio, you may just be suffering from cruft - left over config files. Try removing them:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by CoolJohnB on 2011-03-20
Quote from another thread:

If you open up a terminal and run gconf-editor, go to apps, navigate to gnome-power-manager, click on general, and then uncheck "use_time_for_policy", it will fix the warning messages. Some people (myself included) were also having trouble with it automatically hibernating/suspending when unplugged, and this fixes that issue also.

---

