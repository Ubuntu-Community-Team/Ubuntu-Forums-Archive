---
title: "What happened to choice?"
date: 2011-01-23
forum: Desktop Environments
---

### Post by mwray on 2011-01-23
Ubuntu 10.10 x64.
Pulse Audio is ALPHA on this version at best from it's lack of performance. The following issue isn't the only chipset family I've had issues w/ Pulse audio.

I have a machine w/ a very common audio chipset:
Intel 82801H ICH8 Family HD Audio controller.
I see lots of complaints about this FAMILY of cards not working. (Ditto for the windows world.)

It used to be if one sound system wasn't working, I could remove it,
and try another. (EG> I could use ALSA or OSS, or ESOUND, et. el.) 

Now, apparently XDM,GDM,KDM, KDE,GNOME, and XFCE are "DEPENDENT" upon pulse audio being installed. so if I remove pulse audio, all these packages get removed with it, as being "dependent" upon pulse audio.

I fail to see why whether I have an particular audio subsystem installed or not causes these packages and their cousins (Koffice, Gnome-office, kontact,kmail, kword, ...) to be removed. 

What happened to choice? I would like to try my hand at making ALSA or OSS work w/ my audio system, but am not given the opportunity to do so, as apparently if I re-install any of the aforementioned packages, Pulse-audio comes back.


EVERY variant of Ubuntu and Pulse Audio I have tried causes Audio to fail in FLASH.  So now in 10.10, I'm required to not have audio in flash, because Pulse is broken and I'm not allowed to use another audio system with Ubuntu. I made the move to ubuntu originally because MORE things worked in it than in other variants. Now it seems MORE is broken, and I have to do more jumping through of hoops to make things work, and now, it is broken enough for me to go distro hunting again for the Desktop. 

I'll stick w/ Ubuntu LTS on my server platforms for now, however, it is sad when an issue has already been filed as a bug report numerous times, and from what I've read online, going as far back as October, there has been NO progress...all I see are more people submitting the same issue, with no resolution.

It's also surprising how many audio drivers are blacklisted by default. So i feel sorry to the newbies who are trying out Ubuntu for the first time on slightly antiquated equipment because it's the only spare box they have. They will have a bad taste in their mouths do to many drivers being blacklisted out of the box. (Audio, Networking, Graphics).  It seems to me blacklisting is a hack instead of a fix, especially since apparently the blacklisting isn't done on the Live Cd of the previous version (Luicd works out of the box much better than Maverick).

Now to be fair, I realize more effort went into making sure stuff worked for Lucid since it's an LTS, however, Maverick has been out for awhile now, and I am amazed at how much doesn't work for so many people judging by the amount of complaints on the forums.

I only upgraded from Lucid to Maverick because a power blip corrupted my install.(Ok, clean install of maverick...) and my Lucid DVD was shot to hell, thanks to my "friends" with bad drives and bad disc habits.


If anyone can point to a solution that definitely works a majority of the time for Maverick clean install Intel 82801H audio issue, that'd be great.

Things I've tried include: updating the modules with the latest repository, manually modprobing the drivers. (They load, but don't work).
lshw shows the device, and SOMETIMES the mixer dains to show it as well, but usually it doesn't show up at all. 

Since I was able to address the issue in the past by removing Pulse and replacing w/ Alsa, I thought i'd try again on maverick. No Joy here. Removing pulse removed ALL instances of windows managers, and I am left w/ plain xorg, that cannot be run by a ?DM (xdm,gdm,kdm).

I guess I MIGHT be lucky enough to get fvwm to load, as a window manager, but that's a big step backwards, especially since this machine was built specifically to run Ubuntu-Studio. 

I know, I know, roll back to Lucid. I might, think I'll give Mint another shot first. First time I tried it was for a similar reason, and it had stuff working that ubuntu didn't....

Good job Canonical, thanks for removing so much choice.

---

### Post by cascade9 on 2011-01-23
AFAIK pulseaudio isnt a requirement for KDE, KDM, Xfce, GDM or gnome- 

[http://packages.ubuntu.com/lucid/kde-full](http://packages.ubuntu.com/lucid/kde-full)
[http://packages.ubuntu.com/lucid/kdm](http://packages.ubuntu.com/lucid/kdm)
[http://packages.ubuntu.com/lucid/xfce4](http://packages.ubuntu.com/lucid/xfce4)
[http://packages.ubuntu.com/lucid/gdm](http://packages.ubuntu.com/lucid/gdm)
[http://packages.ubuntu.com/lucid/gnome](http://packages.ubuntu.com/lucid/gnome)

I've seen directions on how to disable/remove pulseaudio from various ubuntu versions. I dont know if the following link will work, but you can try it if you want- 

[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)

---

### Post by kellemes on 2011-01-25
I'm not using Ubuntu so I cannot check if this works..
[https://wiki.ubuntu.com/PulseAudio#PulseAudio Removal]("https://wiki.ubuntu.com/PulseAudio#PulseAudio Removal")

By the way.. I'm not here to get people to ditch Ubuntu obviously, but still I'd like to point out there are more options.
Ubuntu isn't really made for transparency and ultimate control to the end user. So you may consider using another distro.
Personally I'm using Arch for some years, using it's excellent wiki and forum I have found no reason to look back.

---

### Post by mwray on 2011-01-30
:guitar: Update:

Was reading through my configs, and noticed that my system was requesting mods named hda_intel  but there were no mods with that name. Went through the modles directory for ALL of my kernels, (had 5 minor versions of 2.6.35) and all had /lib/modules/version/kernel/sound/pci/hda and the directory was always empty. Nor could I find a separate file to compile this set of modules.  



Downloaded a NEW copy of 10.10. When I booted to the live CD this time, it spent a long time on the internet downloading stuff than the original copy, and low and behold it included the hda drivers in the hda folder (previously empty, now had over 30 files in it.) Also, was able to remove pulse audio (and put back w/out losing Xorg all together. (It's like a different distro almost...so like maybe the mirror I dl'd from actually had a beta or alpha copy of 10.10...as before any attempt to remove pulse would remove everything Xorg related. I could reinstall things like xorg itself and blackbox without pulse, but all the major WM's (XFCE, Gnome, and KDE) were forcing me to use pulse...which is known to sometimes break audio in flash.)   

After that reloaded 10.10 fresh, and audio works with or without pulse in all desktop environments with the exception of a few minimalist enviroments I won't use as they don't even provide a way to start a program outside of your .x* files in your home dir.) Which is a bit TOO minimalistic for me.


Seeing as how both times I downloaded through the canonical download links, I  think it strange that at least one is not the same as the final release as they are supposed to be mirrors. The md5's were different, close, but different.  (Link I used was for Desktop 64-bit version) 
 
I dumped the original copy before I thoguht about saving the info to send it back for inspection...(Arrgh...) I was thinking more along the lines, of not wanting to spread the broken copy...

There is a night and day difference to how well it runs too. ON the surface it all looks the same (same interface, etc.) but the speed, and completeness of support for my hardware is night and day difference. 

(I only do "FRESH" loads I refuse to do upgrades..i keep my data on a separate drive, and my "Customer programs" on another separate drive.)

Yay, now I can move forward with learning C on my favorite platform, and still rock with tunes in the background as I study.


:popcorn: :guitar: =D>\\:D/

---

