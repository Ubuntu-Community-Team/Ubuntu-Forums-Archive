---
title: "This is the sound issue..."
date: 2005-09-03
forum: Desktop Environments
---

### Post by HolyShnikes on 2005-09-03
Ok, I had a post a bit ago about the sound problem I have been having.  [http://ubuntuforums.org/showthread.php?t=62146](http://ubuntuforums.org/showthread.php?t=62146)  Now I am having a different problem.  Not only does the CD Player not have sound but the whole sound system is screwed.  Im not sure what I did to make nothing work, but I was trying to get alsa to work, and thats all I can really remember.  I was trying to many things to recall.  So now I have checked the Hardware information for my sound card and it says that it supports ALSA and OSS, and the sound device being used is ALSA.  This is where it gets tricky.  I tried to reset the sound back to defaults and I get an error message saying ```
Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device.
``` 

What is this about?  What should I try next guys?  Tis a pickle no doubt about it.

---

### Post by mlomker on 2005-09-04
Does lsmod show the modules loaded?
Does /dev/dsp* exist?
Anything interesting from dmesg?
What do you have for settings under 'sound system' in kcontrol right now?  Is hardware at autodect and the check box for 'auto-suspend if idle' checked?

I searched Google and it could be just about anything, given those error messages.

---

### Post by HolyShnikes on 2005-09-04
I checked google and got the same things, I have looked over them already.  They are at where they need to be. I think I need to uninstall the sound drivers and  try to reinstall them.  But I was trying to save that for the last thing to do....

---

### Post by one_ro on 2005-09-04
[QUOTE=HolyShnikes]I checked google and got the same things, I have looked over them already.  They are at where they need to be. I think I need to uninstall the sound drivers and  try to reinstall them.  But I was trying to save that for the last thing to do....[/QUOTE]

Please be aware of what might happen if you do that... I reinstalled my alsa drivers and I am now here:
[http://www.ubuntuforums.org/showthread.php?t=62053](http://www.ubuntuforums.org/showthread.php?t=62053)

(Maybe we could use the same thread if we have the same problem...

---

