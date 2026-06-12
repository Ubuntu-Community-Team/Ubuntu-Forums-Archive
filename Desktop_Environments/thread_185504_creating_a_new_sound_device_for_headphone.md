---
title: "creating a new sound device for headphone"
date: 2006-05-31
forum: Desktop Environments
---

### Post by eigenman on 2006-05-31
Hi,

I have a sound blaster in my computer, and I can play music with it using alsa just fine. However connecting headphone and microphone is a hassle, since the connections are at the back. The SB card does have two distinct line outs, and line out 1 is being used for the speakers. I was wondering how I can make line out 2 dedicated for the headphone. I'm going to use this with skype, so it would be nice if I can create a /dev/dspx device specifically for the headphone and microphone. 

Any ideas?

eigenman

---

### Post by Sutekh on 2006-06-02
You should look into using [udev]("http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html").  

You should be be able to use it to consistently map your microphone/headphone to /dev/dsp#, or to whatever you would like to call them, /dev/microphone for example.

I actually wrote a HOWTO for using udev to control the mapping of devices to persistant device nodes.  I hope it can help.  If not I'm sure I can.

[Ubuntu Forums - Create your own udev rules to control removable devices]("http://www.ubuntuforums.org/showthread.php?t=168221")

---

