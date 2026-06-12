---
title: "Ubuntu freezes while charging"
date: 2011-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sebastian86 on 2011-11-23
hi!

my ubuntu 11.10 64bit (dell e5420) freezes if and only if I plug in the ac adapter AND the battery isn't fully loaded.
So for example if the battery is 80% and I plug in the ac adapter, the mouse (and the laptop itself (music still plays, but the video doesn't)) freezes. When I remove the battery while freezing, everything works fine then. Same happens, if I unplug the ac adater.

Any ideas?

---

### Post by mikeycgto on 2011-12-07
I have same setup (Dell E5420 with Ubuntu 11.10 x64) and have experienced something similar. So far, it hasn't frozen completely, but when I plugin my power cord, things get very sluggish.

The weird part is, the moment I unplug the power cord, responsiveness is restored and things work smoothly again.

Clearly, there is something weird going on here with power management.

Normally, I use a docking station and have no problems with the dock.

---

### Post by BC59 on 2011-12-07
Possible solutions:

Open the System Settings-->Power settings(first option upper right corner).
Play with **Suspend when inactive for** etc to see if there is a difference.

If no, install Jupiter to tweak the settings:

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

Instructions here:
[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by roshats on 2011-12-10
I have Dell e5420 and have this problem too. Has anyone solved this problem?

---

### Post by majhoul on 2012-01-25
Salam,
try ```
echo N> /sys/module/drm_kms_helper/parameters/poll
```

---

### Post by kghunt on 2012-03-05
I am also having the same problem Dell E5420. I have had this issue on every distribution I have tried except the official Dell one (but that is 10.04 and breaks when you update).

Same problem on Fedora all versions and mint (which is ubuntu anyway).

Is there a bug filed for this?

---

### Post by kghunt on 2012-03-06
I have also discovered that if you take the battery out it fixes it instantly...

I need to get this fixed. I can't use my laptop while its charging and I can't charge my laptop while Im using it. So I never have a charged battery.

I don't even know where to start looking.

---

### Post by chicken159 on 2012-03-17
Having googled and seasrched the forums...here is the solution:

Adding the following line in /etc/modprobe.d/local.conf

options drm_kms_helper poll=N     

Then restart. If you want to check it works first...just do this:

echo N> /sys/module/drm_kms_helper/parameters/poll

---

### Post by kghunt on 2012-03-20
> **chicken159 said:**
> Having googled and seasrched the forums...here is the solution:

Adding the following line in /etc/modprobe.d/local.conf

options drm_kms_helper poll=N     

Then restart. If you want to check it works first...just do this:

echo N> /sys/module/drm_kms_helper/parameters/poll

I get permission denied if I try to run the last command. With sudo the same result. So I used nano to change it to N which worked.


Also I do not have this file so how do I make it permanent?

/etc/modprobe.d/local.conf there are only blacklist files in that directory.


Edit - Works with less/more or tail though

---

### Post by chicken159 on 2012-03-20
There's a bunch of threads on this issue, and there is a temporary and a permanent fix. To correct/update my previous post:

A temporary solution which works immediately is:
sudo echo N> /sys/module/drm_kms_helper/parameters/poll

(but see previous post if this doesn't work)

To make this a permanent solution, create/edit /etc/modprobe.d/local.conf to add the following line:

options drm_kms_helper poll=N

Then restart and the problem should go away.

---

### Post by kghunt on 2012-03-21
The above worked. I no longer have the charging issue. But Now my computer does not automatically detect when an external display is plugged in.

---

### Post by chicken159 on 2013-03-18
This fix no longer works after update to 13.04....oh wait, now it does again...sorry!

---

### Post by wildmanne39 on 2013-03-26
Thread closed. Please do not post in old threads.

---

