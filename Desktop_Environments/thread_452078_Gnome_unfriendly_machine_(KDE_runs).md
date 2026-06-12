---
title: "Gnome unfriendly machine? (KDE runs)"
date: 2007-05-22
forum: Desktop Environments
---

### Post by TravMan63 on 2007-05-22
Greetings.

I have been testing Ubuntu CE 7.04, Ichthux 6.09 and Kubuntu 7.04.

Ubuntu is my choice of these three, mainly due to the ease of setting up the codecs needed for video/audio playback...
(The Ubuntu/gnome team has made this very easy to do - good job!)

... and since the machine is going to be used for multimedia presentations (Open office 2.2 works great for this (Ichthux has 2.0, which doesn't have the movie capabilities) this is a key deciding factor.

However, running the live cd (of all 3 distros) - only the kde versions boot up without errors.
The errors are:
"Encountered problem while loading OAFID GNOME_Panel_Trash Applet"
and
"Error starting Gnome Settings daemon - themes, sounds, background settings..."

The 'dock/panels' then become garbled.

I have used the same cd on another system without these problems.  Sound and video play great.

Before I make a HD install, I'd like to know if, or how easy it would be to eliminate these problems.

The system that has problems :
Pentium 3 600 Mhz
256 MB Ram
Intel 82810E video

system that runs better: (screen refresh rate only =61 is a problem this one has)
Athlon XP 1.5 Ghz
1 GB Ram
Nvidia 7600GT (AGP)

The machine is already in use (it was donated to our church), but has an unlicensed copy of windows XP (which is configured to not allow any files or changes to be persistent after rebooting); we're wanting to remove XP completely, and really can't afford downtime.

Any help is greatly appreciated.

Thank you!
TM

---

### Post by scrooge_74 on 2007-05-22
Most likely to run ubuntu would be better to use the alternate CD install since you have the minimum RAM requiere, you should check an Xubuntu CD.

---

### Post by TravMan63 on 2007-05-23
Thanks for the info...

I tried xubuntu, however, it played videos (the ogg supplied in 'samples') - with the colors incorrect.

I installed the codecs (as I did in ubuntu) - and the same files I tested on ubuntu (wmv, mpg, mp3) would not play on xubuntu.

Is gnome "eyecandy" installed by default in ubuntu, could this causing the error?

Ubuntu works much better than xubuntu in my situation


TM

---

### Post by scrooge_74 on 2007-05-23
you need to manually make more changes that normally you dont have to do in gnome.  Still Gnome is a lot more resource intensive than Xfce, you can install the same apps you will use in Gnome

---

### Post by TravMan63 on 2007-05-23
To add support for mp3, wmv and mpg, I added totem.

Then by trying to play the file(s), totem will download the correct codecs (gstreamer)

--> downloading the same gstreamer files for gxine - didn't work.

I'll have to test this on the destination pc - unfortunately, I have no sound on this one
(in xubuntu - it's fine in ubuntu)

gxine - still shows 'bad' colors - playing the same file (Experience ubuntu.ogg) with totem is much better

Hopefully they play ok in Impress.  (which, appears to be an included package on distrowatch, it's not.)

--
edit:
In the add/remove - the app is named 'movie player', not totem.  When it runs, it has totem in the title bar

---

