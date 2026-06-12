---
title: "No sound input via internal, external or USB mic"
date: 2009-04-11
forum: General Help
---

### Post by mxboy15u on 2009-04-11
I can see my usb mic, which is probably the most important to me, but I just cannot get any input audio no matter what settings I play with. I also had this issue with 9.04 but I downgraded to 8.10 hoping this would be cleared. I have an Acer 5315 and am at my wits end with this microphone problem.

---

### Post by tommcd on 2009-04-11
> **mxboy15u said:**
> I can see my usb mic, which is probably the most important to me, but I just cannot get any input audio no matter what settings I play with... 
What have you done so far? List what you have done, and any errors you got.

First, the basics:
With the usb mic plugged in, run in terminal: **lsusb**. This will list all usb devices that Ubuntu sees, in order to verify that the mic is detected.
Did you try running **alsamixer**? Run alsamixer and make sure the mic channel is unmuted, and turn the sound level all the way up for the mic.

---

### Post by mxboy15u on 2009-04-12
If I run alsamixer it will not let me unmute it. I can unmute if I use the graphical sound control but that does not result in any sound going out in skype or me being able to record using the application that is installed with ubuntu. It does show that there is a USB mic in skype when I connect it, and the camera attached to the mic works fine. I will do that command and post back.

---

### Post by mxboy15u on 2009-04-12
Bus 002 Device 003: ID 0471:0333 Philips 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


It seems to be recognized, and when plugged in the volume control shows it and allows me to mute/unmute and adjust the volume. There is no output though and the volume level always drops back to 0 (I assume from lack of audible input?) or mutes itself.

---

### Post by tommcd on 2009-04-12
Is this the output of lsusb? I really don't see the mic in there. Try lsusb with the mic plugged in and with it removed to see if there is a difference.
Here is a long discussion about your laptop. There is some limited advice for the microphone problem in post #56 of this thread:
[http://ubuntuforums.org/showthread.php?t=610603](http://ubuntuforums.org/showthread.php?t=610603)

---

### Post by mxboy15u on 2009-04-13
Ok, thanks for the help and that thread is great! I did find out my problem however, this whole time I have been maxing my volumes thinking that was the problem, well with the volume turned all the way down it works perfectly. I knew it was something stupidly simple but I am so glad that my computer is working flawlessly now. Thanks again!

---

