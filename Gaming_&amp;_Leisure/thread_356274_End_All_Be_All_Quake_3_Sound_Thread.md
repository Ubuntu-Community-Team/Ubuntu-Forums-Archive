---
title: "End All Be All Quake 3 Sound Thread"
date: 2007-02-08
forum: Gaming &amp; Leisure
---

### Post by ghandi69_ on 2007-02-08
Hi All,

I've been trying to get sound to work in quake 3 for about the past 3 days with no luck.  I have tried all of the following known solutions on this forum..  I'll explain in a little more detail.  The error when starting the game shows up in the terminal as 

> Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp


This does not stop the game from being playbale.. you just can't hear anything.  I have tried the following steps

> sudo echo "guake3.x86 0 0 direct > /usr/local/card0/pcm0p/oss

note also.. I usually just go in and edit the oss file manually, and I also do the same command with disable instead of direct in the pcm0c oss file.  I have no idea why to do this, but when run, quake 3 will start up with sound. but will crash usually as soon as the skirmish is started.

I have also tried going to my ~/.q3/baseq3/q3.confile file or whatever and changing my

seta snddevice = "/dev/dsp"

to dsp0, dsp1, dsp2, adsp0, adsp1, adsp2.. and so on..

this fix for me appears to have no effect.

There is also a method I have found in these forums for installing 3rd party binaries that fixes the issue.  But then you lose internet community gaming support...

Now, on to the possible fix... apparently 

> f anyone's interested, the solution was to add -fno-stack-protector to the CFLAGS variable in the Joss makefile and recompile it.

except.. I do not know how to do this.. could someone give me instructions for how to do this last step?  Thanks!

---

### Post by Keymone on 2007-10-28
i have same problem...

nobody playes Q3? =(

---

