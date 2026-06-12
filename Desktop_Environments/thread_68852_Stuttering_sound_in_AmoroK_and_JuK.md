---
title: "Stuttering sound in AmoroK and JuK"
date: 2005-09-24
forum: Desktop Environments
---

### Post by BoHu on 2005-09-24
I have an AMD 400MHz proc with 512MB of RAM. I get stuttering sound in AmoroK and JuK. They both act as if my computer isn't powerful enough to run them but I know that can't be. I run iTunes/Windows2000 on this same computer and it works fine.

What might be the problem? Maybe DMA is off? Maybe some other program stealing cpu cycles? Maybe sound buffer too small? I don't know how to check these things. I keep looking but can't find settings for any of these things.

---

### Post by mo_x on 2005-09-24
Look in the KDE Control Center -> Sound & Multimedia -> Soundsystem. I had a problem with stuttering sound that was solved by setting the sampling rate to 48000 Hz.
What soundcard do you have?

---

### Post by mlomker on 2005-09-24
>  Maybe DMA is off? Maybe some other program stealing cpu cycles? Maybe sound buffer too small?

There is a lot of information in the [Ubuntuguide.](http://www.ubuntuguide.org) I also have a post [here](http://ubuntuforums.org/showthread.php?t=64961) regarding dma.

Go into the Control Panel, Sound & Multimedia, then Sound System.  Make sure that the Realtime Priority checkbox is checked.

---

