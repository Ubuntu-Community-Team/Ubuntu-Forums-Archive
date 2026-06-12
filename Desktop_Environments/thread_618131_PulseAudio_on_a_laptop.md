---
title: "PulseAudio on a laptop"
date: 2007-11-20
forum: Desktop Environments
---

### Post by MeanderingCode on 2007-11-20
I'll try to be to the point.  I'm trying to offer my success and ask for help to polish up my setup.

I (obviously) wanted to play sound over the network to hear it from the speakers attached to the desktop computer.
I installed pulseaudio and got it working (thanks to [this]("http://forums.debian.net/viewtopic.php?t=12497") thread [forums.debian.net] and the [PulseAudio website]("http://www.pulseaudio.org/"))

During the course of discovery, i read that pulseaudio was sometimes unfavorable on laptops because it "plays silence" when nothing is playing...sure enough, staring a top in a terminal showed me that it is *always* using just a little bit of cpu (at least when run with the high-priority flag enabled (priority of -2 and nice value of -15...this seems often important to avoid choppy sound...at least over my wireless connection).  So...

I wrote two scripts (ha, barely qualify) in order that i could easily flip back and forth between ALSA as itself and my pulseaudio setup (which wraps alsa, and everything, so i don't have to mess with some things not playing nice, nor switch individual application settings every time i toggle pulseaudio)  Not all applications needed me to go through each of these command lines in order to work after a toggle (on or off), but i found that all work after i do.

BEFORE YOU COPY, PASTE, AND RUN THESE SCRIPTS, realize a few things:
1.  THIS IS NOT A HOW-TO.  i don't know if you have a working setup, what your setup is, or if you have all the software i have installed.
2.  HAVING SETTINGS IN /etc/asound.conf WILL PROBABLY CONFLICT WITH THIS SETUP.  That conf file is system wide...asoundconf unset-pulseaudio doesn't configure your user's asound stuff, just removes reference to pulseaudio in your home dir config file
2.  THESE SCRIPTS PROMPT FOR YOUR PASSWORD VIA SUDO.  I'll tell you why, but first i should say that you should WRITE PROTECT THEM, EVEN FROM YOUR OWN USER, because, if you use them all the time, you will be running who-knows-what if they can be modified...all you see is a password prompt.  I need root privileges to run the pulseaudio daemon at incredibly high priority and nice value so my sound is continuous.

Without further ado:
pulseon
```
#!/bin/bash

asoundconf set-pulseaudio
sudo pulseaudio --system=1 --high-priority=1 -D
padevchooser &
```
pulseoff
```
#!/bin/bash

killall padevchooser
sudo killall pulseaudio
asoundconf unset-pulseaudio
```
Tada!  Impressed?  Be impressed by the folks that brought you avahi, pulseaudio, and asoundconf, cause *they* are magic...*I'm* just too lazy to type three lines of code when i'm working on my laptop at home :wink:
NOTE: Toggling while applications are running and/or playing can cause odd behavior...if you run into trouble, close all applications that connect to alsa, esd, whatever (i.e. play audio) and re-open, see if they work now.

Now, here's my trouble:
I run XFCE (Xubuntu 7.10) and like to have the xfce4-mixer-plugin on my panel.  I believe this is calling out to esd.  Now esd is replaced on my system by esdcompat, which is a package (and script) that calls out to pulseaudio because PA wraps esd.  What this means is that, even though i've stopped pulseaudio's autostarting via init script, when i log in to xfce and the mixer applet starts, esd (and therefor pulseaudio) get called to start.  How do i stop this in a graceful and not hacky way?

---

### Post by MeanderingCode on 2007-12-05
Can anyone offer me a solution?

I need to have pulseaudio *not* start until i say so, but (short of removing references to esd, then replacing them, or something similarly silly) i cannot figure this out.

Or, is someone fixing the pulseaudio "play silence" problem to make it eat less cpu time?

It's a problem, and one i am not qualified or knowledgeable enough to do anything about.

---

