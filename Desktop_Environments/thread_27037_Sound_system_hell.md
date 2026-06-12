---
title: "Sound system hell"
date: 2005-04-14
forum: Desktop Environments
---

### Post by ziphnor on 2005-04-14
Hi,

After installing Ubuntu, i couldnt log into gnome, i just got some stuck sound playing in gdm, and if i logged in, a brown screen with a working mouse cursor.

I installed KDE and could login into that, but the sound was still there. I then swapped gdm with kdm, and it disappeared. However i was only able play sound in XMMS and "Music Player", the first with EITHER OSS or ALSA, but NOT esd, and in music player only with gstreamer, and it would crash horribly otherwise. 
Since im coming from gentoo where i just used alsa and alsa mixer(ive never heard of arts/ESD/gstreamer before) and everything worked great i tried to use the tips in [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) regarding using ALSA without ESD, and now i can only use the OSS plugin with XMMS, the ALSA plugin only gives me some stuck sound bit(which stays until i reboot). To put it another way, im totally screwed, i cant login to Gnome and i cant play sound with anything else than XMMS.
It seems its ALSA thats the problem now, if i restart ALSA, the annoying sound stops for a second until ALSA restarts.

My sound card is common as dirt: A SBLive! Value PCI card which have worked without me doing anything in Redhat, Mandrake and Suse.

Im hoping someone knows how to properly setup ALSA and remove other sound system bits that i dont need. 

As far as i can tell from 'top' artsd is running when in KDE, for all the good it does.

So how do you say ... Ah yes : * HELP ! *

---

### Post by cwaldbieser on 2005-04-14
Are there specific applications you are trying to get sound to work in besides the desktop manager?  Since a lot of apps try to use the sound card in different ways, sometimes multiple configurations need to be tweaked.  I have several games that shared common sound libraries I needed to configure, though I eventually got everything working through esd.

I am at a loss as far as your gdm problems are concerned.  Do you feel comfortable enough trying to log into a console session and starting the graphical display from there?  That might give you some additional useful clues.

---

### Post by ziphnor on 2005-04-14
Im not using any games at all, only xmms/xine and similar applications.

I dont mind a console session at all, how do you think i  got KDE installed? :) However usually you have to kill X first if you want to start from the console which can be a pain.

I already checked gdm and the X servers files in /var/log/  but there doesnt seem to be any errors. I dont think starting from the console will be much help, im guessing it will manage to show X before encountering problems, and leave me stuck there. Shouldnt there be a log file somewhere?

Im surprised that the sound system stuff is so complicated, as i mentioned earlier, on Gentoo all i did was 'emerge alsa-utils' basicly(since my card is supported  by a kernel  driver) and it just worked. I never had any problems with sound whatsoever. I might just have been lucky though, or it could be the magic of the USE flags on gentoo, that makes sure to compile programs with ALSA support.

 I think ill try a reinstall, but i wont deny that right now i also have Fedora Core 3 CD and a Gentoo 2005 LiveCD on my desk, and im sort of considering going back to Gentoo since it works so well if you just follow the installation documentation.

On the other hand a few month from now im probably upgrading my system, and i dont want to waste too much time on installation right now. Perhaps i should just try to use Fedora and see if i can survive the horrible RPM package system....

---

