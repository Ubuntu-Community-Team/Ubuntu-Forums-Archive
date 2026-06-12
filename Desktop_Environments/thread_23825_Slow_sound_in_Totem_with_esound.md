---
title: "Slow sound in Totem with esound"
date: 2005-04-04
forum: Desktop Environments
---

### Post by MaX on 2005-04-04
I'm running most current hoary since yesterday and since two weeks now the sound has been out of sync when playing movies with totem,

I installed kubuntu yesterday too and I assume it runs arts and that worked great.

Previously I've used ALSA as my soundoutput but since yesterdays update I don't have the gstreamers output thingy in my menu anymore.

What happened??? Two weeks ago I could use both Esound and Alsa and get synced movies now I can't. 

(actually now I really can't since I get Error 17 in Grub and I can't mount my reiserfs partition from the livecd either. ](*,))

---

### Post by titus on 2005-04-13
i have the same problem with esd in both mplayer and totem.

i want to try to switch to alsa.

---

### Post by Dr Gonzo on 2005-04-13
Well, Totem does use esound by default, so if you're having problems with that, I'd suggest using something else.  Xine has audio output options, so you could use it.  However, esd will attempt to take over your sound card all the time.  In order to switch to the ALSA output plugin, you'll have to change esound to only spawn when an application calls it.

Here's what the wiki says to do:> [SIZE=1]To work around this problem, esd must be configured to release the sound card when it is not using it. To do this, edit /etc/esound/esd.conf and change the line that begins with spawn_options to begin with default_options. Then, change the -as 5 to -as 2. Finally, remove the two bottom lines about default_options and change auto_spawn=0 to auto_spawn=1. Note: this problem only occur[/SIZE]

You can also install totem-xine, which will use the xine engine instead of the gstreamer framework.  I find it more robust in many ways.

Hope this helps.

Note that I run Hoary, and I don't have the same problem.  :( :)

---

### Post by titus on 2005-04-14
Okay done, that seems to work quite well, mplayer with -ao alsa now works without 'killall esd'.

thanks.

---

