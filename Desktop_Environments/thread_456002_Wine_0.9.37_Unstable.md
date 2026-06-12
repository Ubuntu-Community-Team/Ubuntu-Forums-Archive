---
title: "Wine 0.9.37 Unstable?"
date: 2007-05-27
forum: Desktop Environments
---

### Post by blue_shift on 2007-05-27
I've installed wine 0.9.37 from the official site, and it seems to be highly unstable. When running "wine desktop" windowed, focusing on another window will cause an x server crash. Seems to be something to do with sound - the first time it happened there was a crash report for the sound server on login.

Furthermore, winecfg now gives this:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

and when trying to adjust sound settings:
```
/bin/sh: /usr/bin/esd: not found
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

```

I have a libjack package installed.

I'm running kubuntu 7.04

Finally, when running rollercoaster tycoon 2 trying to save (interacting with the hard disk) causes an access violation when trying to write to ./wine/drive_c/* and read from /home/user/*

Thanks.

---

### Post by takayuki on 2007-05-29
hi,

i had a 
```
/bin/sh: /usr/bin/esd: not found 
```

error also when trying to use gconf-editor.

```
sudo aptitutde install esound
```

fixed it.  hope that helps.

---

### Post by blue_shift on 2007-05-30
Thanks, it's cleared up the error nicely. I'll test if it makes this thing any more stable.


Just this to contend with now..
```
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

---

### Post by dez_cole on 2007-06-01
> **blue_shift said:**
> Thanks, it's cleared up the error nicely. I'll test if it makes this thing any more stable.


Just this to contend with now..
```
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

When i got that error i did this and it fixed it...

Install libjack0.100.0-0 through the terminal by ```
sudo apt-get install libjack0.100.0-0
```

then enter this code in. ```
sudo cp /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so
```

i found that info in another thread after searching for a while... someone should really make a thread specifically for fixing this error because it seems pretty common.

I hope this helps you!!!

---

### Post by blue_shift on 2007-06-02
Thanks for the tip, but it seems there's an apt issue somewhere:

```
alex@alex-desktop:~$ sudo apt-get install libjack0.100.0-0
Reading package lists... Done
Building dependency tree
Reading state information... Done
libjack0.100.0-0 is already the newest version.
libjack0.100.0-0 set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15 binfmt-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

In case it was there anyway:

```
cp: cannot stat `/usr/lib/libjack.so': No such file or directory

```

Could someone explain the "manual version" business?

Thanks.

---

### Post by LK_gandalf_ on 2007-06-05
Hi all, I have the same problem. When i run winecfg and go to the sound tab I receive:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

```

If i run *sudo cp /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so*
I have in response
*cp: `/usr/lib/libjack-0.100.0.so.0' eand`/usr/lib/libjack.so' are the same file*

How can I fix these problems?
Thank you ;)

---

### Post by burt_57 on 2007-06-06
> **dez_cole said:**
> When i got that error i did this and it fixed it...

Install libjack0.100.0-0 through the terminal by ```
sudo apt-get install libjack0.100.0-0
```

then enter this code in. ```
sudo cp /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so
```

i found that info in another thread after searching for a while... someone should really make a thread specifically for fixing this error because it seems pretty common.

I hope this helps you!!!

Well thank that did fix the error about libjack :popcorn:

---

