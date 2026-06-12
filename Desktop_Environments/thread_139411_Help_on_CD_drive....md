---
title: "Help on CD drive..."
date: 2006-03-04
forum: Desktop Environments
---

### Post by JDHarms on 2006-03-04
My CD drive is very, very slow.  I'm on a dell laptop, and the CD drive never rips at a speed of more than 2.0X!

Also, on the CD I'm ripping, it hangs 77 percent of the way through the third to last track.  I can't figure out why.  It also hangs 77 percent of the way through when playing it.  Are there any patches or drivers I need to download?

--Daniel

---

### Post by stuporglue on 2006-03-04
Have you adjusted turned on DMA? 

Check the man page for hdparm, that should speed things up if the drive is capable of going faster.

---

### Post by JDHarms on 2006-03-04
Do you mean to turn on DMA?  I checked the man page, but cannot figure out hat to do.  Can you explain a little more in depth?

---

### Post by akiro.yamamoto on 2006-03-04
Type this ```

sudo hdparm /dev/hdc -d1 (Or whatever your CD-Rom drive is)

```
The "-d1" should enable dma for that drive.
And post the results

---

### Post by JDHarms on 2006-03-04
/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


That's all I get.  Do I go about turning on DMA?  How?  I greatly appreciate your help thus far!

--Daniel

---

### Post by JDHarms on 2006-03-04
I figured it out!  Sort of....

You had the order of the arguements backwards, it's arguement, then device.  So, with:
sudo hdparm -d1 /dev/cdrom:

I got this:

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

The problem is, this doesn't fix it.  It's still terribly slo, and it feels like it's slowing itself down, as if it's limiting it's own speed.

I already have the cd speed set to default.

--Daniel

---

### Post by JDHarms on 2006-03-04
Anyone?

---

### Post by JDHarms on 2006-03-04
one last try.  Bump.

---

### Post by chemgoode on 2006-03-27
JDHarms
I just looked into this problem myself today.  The slow speed is probably due to the paranoia setting for sound-juicer (or whatever ripper you are using).  I adjusted mine using gconf-editor (Applications > System Tools > Configuration Editor, or just "gconf-editor" in a terminal).  Expand the apps folder and highlight sound-juicer.  The paranoia parameter should be visible - double click to bring up a dialog box that will allow you to adjust the setting.  The default is 4 and decreasing the value should increase the ripping speed.  I set mine to 1 and so far so good.  The ripping speed jumped from 2 average to 7 (for ogg-vorbis encoding).  I got this info from this [thread]("http://ubuntuforums.org/showthread.php?t=92940&highlight=cd+rip+gui").
I hope this helps...
-david

---

