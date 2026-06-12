---
title: "Problems with Logitech Quickcam Express"
date: 2005-12-27
forum: General Help
---

### Post by The Miker on 2005-12-27
I've looked all over the internet for a solution that actually works, but none have. So, here's the deal. I've tried using the good ol' quickcam.sh and even spca5xx, but nothing works right.

For anyone who wants to know, this is my webcam:

```
ID 046d:0870 Logitech, Inc. QuickCam Express
```

And the kernel I'm using is 2.6.14-ck1.

The only thing I've had moderate success with is the quickcam.sh script...well, not quite. I installed qc-usb-source with apt-get and did 'make all' and 'insmod ./quickcam.ko'...no problems. A quick look at dmesg tells me all is well, and that /dev/video0 has been successfully mapped to my camera. Then I try v4l-conf, and it gives me this:

```
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1152x864, depth=16, bpp=16, bpl=2560, base=0xe0000000
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Unknown error 515
/dev/video0 [v4l]: no overlay support
```

Hmm...not good eh? So, I figure, why not, just for the hell of it I'll try xawtv -noscale -noxv -c "/dev/video0". I was greeted with a bunch of crap about not being able to use the device for whatever reason...the latest was "no space left". Odd. Then after that, I'm no longer able to use the camera for anything. If I try to run v4l-conf or xawtv again, it just hangs, and I can't even unload the module because it's "in use"...which is odd because xawtv was fully closed after it messed up.

Long story short, I'm growing increasingly frustrated, all I want is a working webcam. Any suggestions?

---

### Post by oskude on 2005-12-27
hi,

i got a webcam (pixart) thats supported by "spca5xx" but the module in breezy didnt work.

so i used "easyspca" from here [http://ralph.n3rds.net/index.php?/archives/124-Webcam-installation-scripts.html](http://ralph.n3rds.net/index.php?/archives/124-Webcam-installation-scripts.html)
and now the webcam works.

you could also try "easycam" from here [https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

---

### Post by The Miker on 2005-12-27
Well apparently spca isn't for my webcam, it's for newer Quickcam Express models...the correct driver is qc-usb according to everything I've read.

I've tried easycam but it just does the same exact thing as using quickcam.sh or even installing quickcam.ko manually.

I'd like to add that I tried my webcam last night, and it's **still** saying that I can't unload the quickcam module because it's in use, when it obviously isn't!

---

### Post by rwabel on 2005-12-28
thanks oskude for mentioning my blog and our webcam entry in the wiki :-)

@the miker
I've made a new entry about webcams: [http://ralph.n3rds.net/index.php?/archives/128-ubuntu-webcam.html](http://ralph.n3rds.net/index.php?/archives/128-ubuntu-webcam.html)

or check the wiki again. The developer made easycam and it supports several different drivers. It autodetects your webcam or should :-)

---

### Post by The Miker on 2005-12-29
Well, I've already said that I've used easycam, and it ends up just executing quickcam.sh, which I've already done. The driver installs itself with no problem, the problem is getting the bloody device to WORK.

---

### Post by rwabel on 2006-01-05
maybe your webcam isn't supported yet by this script. You can send the guy on the french forum your information so he can add it

---

