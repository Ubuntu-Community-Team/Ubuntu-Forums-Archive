---
title: "What I had to do to get Ubuntu Dapper to where I wanted it"
date: 2006-08-01
forum: Desktop Environments
---

### Post by rmjb on 2006-08-01
This thread is for me to document the extra things I had to do to Ubuntu to get it to fully use my PC. I'll try not to put esoteric things in here like MythTV just things I had to do to get my stuff working how I think they should.
I'll add to it as I go along, and start a new thread (or update this one) when Edgy comes out, hopefully there'll be less things listed then.

[SIZE="2"]**-. Had to install dmraid to get access to my SATA RAID drive**[/SIZE] [ref.]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")
I think this should be installed by default since people use their SATA RAID features, and it should be supported better in the installer. If EVMS can ship with Ubuntu I don't see why dmraid can't, unless there's some stability issues I'm unaware of.
NB. My Ubuntu is installed on a PATA disk, Windows is on the SATA RAID.

[SIZE="2"]**-. Try to get GRUB to boot to my Windows XP that's on the SATA RAID**[/SIZE] [ref.]("http://www.ubuntuforums.org/showthread.php?t=222884&highlight=sata+raid")
If dmraid support is added by default this problem should solve itself.

[SIZE="2"]**-. Install the smp kernel to properly use my Dual Core**[/SIZE]
Maybe the installer should detect for a Dual Core or multi-processor machine and install an smp kernel initially if needed.

[SIZE="2"]**-. Use EasyUbuntu to install multimedia support, flash & java and support for other archives.**[/SIZE] [ref.]("http://easyubuntu.freecontrib.org/")

[SIZE="2"]**-. Set my Audigy as the default sound card, not just in Gnome, but system wide**[/SIZE] [ref.]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=Configuring+default+soundcards") halfway down first post.
In my Gnome Sound Preferences I can choose a default sound card, but that only affects applications in the Gnome world, things like flashplayer still played through the onboard sound. Using the info in the reference linked I was able to set the onboard as secondary.
Why not just disable the onboard sound? Because it's hooked up to the front audio ports and I hook my headset up to that for VoIP/games, etc.
The instructions there aren't complex, perhaps the Sound Preferences tool could do this automatically.
Note: I couldn't find a way to go this through a GUI in Kubuntu like I did in Ubuntu, one of the reasons I chose Ubuntu.

[SIZE="2"]**-. Set up the other buttons on my Logitech mouse**[/SIZE] [ref.]("http://www.ubuntuforums.org/showthread.php?t=219894")
Again, these steps could be done programatically. Logitech or someone should do up a little GUI tool for this.

[SIZE="2"]**-. Get my X800 to be properly accelerated**[/SIZE] [ref.]("http://www.ubuntuforums.org/showthread.php?t=204910")
A lot of people had problems with this guide but it worked for me without problems. Had to recompile when I installed the smp kernel though.

[SIZE="2"]**-. Replaced gnome-screensaver with xscreensaver**[/SIZE] [ref.]("http://www.ubuntuforums.org/showthread.php?t=216154")
This was done because gnome-screensaver wasn't accelerating the rendering even though the proprietary ATi drivers were installed.

[SIZE="2"]**-. Set UTC=no in /etc/defaults/rcS**[/SIZE] [ref.]("http://ubuntuforums.org/showthread.php?p=1336118")
Since I dual boot I noticed the time in Window and Ubuntu was always off. The fix was simple... when I found it. Apparently this question was removed from the installer, even if it's not in the installer it should be in some System Options GUI tool somewhere.

------------

That's it for now, there may be others and I'll add them as I remember them or as they happen. Feedback is appreciated.

- rmjb

---

### Post by T700 on 2006-08-01
Excellent list!  Thanks for keeping such detailed records.  This will serve nicely as a reference for others.

Paul

---

