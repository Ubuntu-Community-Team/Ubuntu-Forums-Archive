---
title: "High pitched sound"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Unununium on 2005-05-05
I installed Ubuntu 5.04 and it makes a constant high pitched sound.  It is not too loud but annoying.  The noise stops anytime that the system is working.  For example, if I click on a link, icon, drop down menu etc. it will stop for a split second.  Another example is if I open a program, the sound goes away until it is fully loaded and the system is sitting idle, then it starts again.  I know it isn't my hardware as I have dual boot with Windows on another hard drive that doesn't make a sound.  I have even switched hard drives thinking that it may be the hard drive that Ubuntu is on.  Right now I am running off of the Ubuntu Live CD which isn't using the HD, so I have eliminated that.  Is there some setting in Ubuntu that needs to be changed?

Oh, lastly, it doesn't go away if I mute everything in the volume control either.

Thanks for your help!

---

### Post by cwaldbieser on 2005-05-06
Is the sound coming from the speakers, or is some other part of the computer making the noise (like CD ROM rubbing something or hard drive making dying sounds)?  If you have a deskop, try unplugging the power to the speakers and see if you can still hear it.  Once you determine what is making the noise, then maybe someone can help you correct it.

---

### Post by trash on 2005-05-06
happened to me once, right after I installed an Adaptec scsi card on my G4(os9 a few years ago)... i found that it was so annoying that I just removed the card and I haven't tried it since nor have i tried it in linux. I do remember that I called apple but they didn't have any answers for me.

---

### Post by Unununium on 2005-05-06
The sound is coming from my speakers, however I am pretty sure that it is a software problem within Ubuntu.  My logic in thinking this is that the sound is only present when I run Ubuntu.  The only difference in the hardware that Linux uses and Windows uses is that they are on two different hard drives.  As I mentioned before, I know it isn't the hard drive as I was using the Ubuntu Live CD to run Ubuntu rather than the hard drive and I got the high pitched noise as well.  It stops whenever a program/command is being executed and only makes the noise when it sits idle.  I am in Windows right now and it is quiet as ever.  By the way, it never changes its frequency.  It never speeds up or slows down.  It is very consistent until the OS is processing info. (i.e. opening a window, loading a web page, etc.) then is stops.  Thanks for your help!

---

### Post by cwaldbieser on 2005-05-07
OK, do you know what sound system you are using (e.g. esound, ALSA, OSS, etc?).    You could try stopping the sound system and see if the noise stops.  If so, you could try experimenting with other sound systems.

If that is not the problem, maybe the driver you are using for sound is causing the problem.  I am no expert in this field, but you could try:

```
$ lspci | grep snd
```

and see if anything looks odd, to you.  Not sure what your experience with Linux is, but this should show you what sound modules are loaded, and maybe you would notice if something that didn't sound like your sound hardware was loaded.

---

