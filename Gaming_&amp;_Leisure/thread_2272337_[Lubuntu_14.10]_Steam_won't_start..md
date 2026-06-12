---
title: "[Lubuntu 14.10] Steam won't start."
date: 2015-04-06
forum: Gaming &amp; Leisure
---

### Post by Drazhok on 2015-04-06
Hi, I'm fairly new to Linux as a whole. I installed Lubuntu 14.10, then I installed Steam. Steam started, then it gave me a couple of OpenGL errors. Now I can't even start Steam. I've searched everywhere and tried every supposed workaround, but none of them work. I have an AMD Radeon HD 4670, and I can't find the legacy driver that works. The one from the actual AMD site doesn't, and the makson96 PPA didn't work either, so I'm stuck with the open source drivers. I got the errors when I had fglrx.

---

### Post by Drazhok on 2015-04-06
bump :(

---

### Post by R33D3M33R on 2015-04-06
Please provide additional info: Which errors? What does it mean that you can't start it? Does it show anything? etc.

---

### Post by Drazhok on 2015-04-06
I open the icon, nothing happens.

At first, it was that OpenGL direct processing wasn't enabled or something.

If I run Steam in the terminal, I get this:

Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME is enabled automatically
[2015-04-05 23:46:36] Startup - updater built Mar 23 2015 20:05:07
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

I assume it's a video driver error, but I don't know how to install the proprietary legacy drivers, since the previously mentioned PPA doesn't work for me.

---

### Post by Drazhok on 2015-04-06
Bumping again, would really appreciate some help. :p

---

### Post by Drazhok on 2015-04-06
Bump.

---

### Post by QIII on 2015-04-06
While we have relaxed the 24 hour bump rule, please do not abuse the new rules.

Three hours is precious little time for a world wide community to react.  Bumping too often comes off as impatient and rude.

---

### Post by Drazhok on 2015-04-06
> **QIII said:**
> While we have relaxed the 24 hour bump rule, please do not abuse the new rules.

Three hours is precious little time for a world wide community to react.  Bumping too often comes off as impatient and rude.

Sorry.

---

### Post by R33D3M33R on 2015-04-07
Remove website version of Catalyst:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

If the above doesn't work, purge the Makson PPA as only 13.04 and below are supported:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:makson96/fglrx
```

(Re)Install mesa:

```
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
```

Reboot.

---

### Post by Drazhok on 2015-04-07
> **R33D3M33R said:**
> Remove website version of Catalyst:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

If the above doesn't work, purge the Makson PPA as only 13.04 and below are supported:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:makson96/fglrx
```

(Re)Install mesa:

```
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
```

Reboot.

Now when I try to run Steam in the terminal, I get:

Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

---

### Post by R33D3M33R on 2015-04-07
Try this now: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

---

### Post by Drazhok on 2015-04-07
> **R33D3M33R said:**
> Try this now: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

At first it updated then gave me the same errors, then I tried again and it works now. Thank you so much. I tried that fix before and it wasn't working, but I guess some files must have changed since I've been fiddling with it.

---

