---
title: "nonfree flash-plugin + firefox = no audio output?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by play0r on 2006-06-23
i'm exhausted from my efforts to fix this problem, so here i am.
i've searched the forum & wiki very extensively for a work around & or fix for this, & yes i noticed the bug report filed a week or two ago.
i just want to know if i should keep attempting to hack away at the problem & see if i can get to a resolution, or just wait for the release of flash 9 in "early '07"?
i've reinstalled flash using first the *.tar.gz package from macromedia, the ubuntu repo, & then finally as a last ditch effort automatix. 
i've used the following dsp wrappers: esd, aoss, auto, arts, & none in my firefoxrc. 
i've attempted to make symbolic links of several things for instance, libesd.so.0>libesd.so.1, & making a sym link when the session starts up in my /tmp (don't have the exact syntax/filenames atm i'm at school, something to do with esd).
i've also reverted to the stock ubuntu kernel to see if it had been something i had done while compiling & moding the 2.6.17 kernel, & it's the same using the stock kernel image as it is using my kernel image.
i have proper audio output in every format of embedded video/audio, except flash. though it views the flash animations/videos seamlessly, no choppiness or glitches. 
i can download the *.flv file from youtube.com for instance using the video downloader plugin (still no audio output though if i attempt to view the video in totem or vlc) & then convert it to *.mpg by using ffmpeg & then view the video with audio output in all its glory, but that is not a solution to my problem... just a temporary fix of sorts.
i noticed this to when i enabled esd in the system>preferences>sound for fun. it has my onboard via chipset as the default soundcard & it will not use my pci as default, whether esd is enabled or not. alsamixer on the other hand has my pci as default. 
also, i have my onboard disabled in the bios & i have no audio cords leading to said soundcard, & yet it still produces sound when that chipset is selected in the system>preferences>sound... any ideas there?
if someone could produce some enlightening words of wisdom or a fix & or workaround for my problem, it would be much appreciated!

ez,
play0r

---

### Post by arnieboy on 2006-06-23
try this:
[http://www.ubuntuforums.org/showpost.php?p=1172405&postcount=175](http://www.ubuntuforums.org/showpost.php?p=1172405&postcount=175)
after pasting the required line, press the following key combos to save and exit:
ctrl-X
Y

---

### Post by searayman on 2006-06-23
i use the website [www.meebo.comfor](www.meebo.comfor) aim and its flash, and my sound also dosent work on it. ANd it really annoying!

---

### Post by play0r on 2006-06-23
> First Posted by arnieboy:
try this:
[http://www.ubuntuforums.org/showpost...&postcount=175](http://www.ubuntuforums.org/showpost...&postcount=175)

i've attempted that already, but i'll give it another whirl since the last app i used to install flash was automatix.

thanks,
play0r

p.s.
any other ideas would be supercool!

---

### Post by play0r on 2006-06-23
i fixed it in strangest mannor i can imagine...
i just removed the plugins from each directory in which they existed, went to google video clicked the download plugin, & let firefox do it for me...
though this isn't a **good** solution... but it fixed it?

ez,
play0r

---

