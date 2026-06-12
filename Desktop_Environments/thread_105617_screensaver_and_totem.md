---
title: "screensaver and totem"
date: 2005-12-18
forum: Desktop Environments
---

### Post by emerick7 on 2005-12-18
I've been looking around but haven't found a solution, so I was wondering if anybody's been able to have their screensaver enabled, but during video/music playback via totem the screensaver does not activate.  It seems like a problem that could have an easy answer... thanks, ty.

---

### Post by emerick7 on 2005-12-20
does anybody have any ideas??

---

### Post by emerick7 on 2005-12-21
So if nobody knows a way, do I send something like this to bugzilla?  I've never used that before, and I'm not sure if that's the place I should go.

---

### Post by farnsworth on 2005-12-21
Hi emerik,

I assume that while playing video, totem (and vlc, mplayer, etc.) have a higher access level to the display than certain other window-manager functions.  Ideally, for me at least, the x-server would wait for the player to finish before blanking the screen or starting the screensaver. I watch movies in bed all the time, and the screen blanks ten minutes after the video's finished; a bug for some, a feature for others.  If you'd like the screensaver to activate during video playback, you'll probably have to talk to an Xwindows guru.

When it comes to music, though, it might just be a peculiarity of totem.  I play all my music with xmms, and the screen will blank with the music playing.  You might just try another music player.

---

### Post by dafrabbit on 2005-12-21
I believe this is being worked on for dapper? Basically what needs to happen is for Totem to send out signals via DBUS to notify the screensaver that it's playing and to not engage the screensaver. At the moment I don't think there is any way to do this automatically with totem (aside from disabling the screensaver manually every time you play something). The way mplayer handles this is by continuously sending key presses so that the screensaver doesn't think the computer is idle.

---

### Post by khc on 2005-12-22
I suppose this can be worked around by having a wrapper script that disables xscreensaver before starting totem and reenable the screensaver after totem is quit. It's not very elegant, but it will work

---

### Post by emerick7 on 2005-12-22
[QUOTE=khc]I suppose this can be worked around by having a wrapper script that disables xscreensaver before starting totem and reenable the screensaver after totem is quit. It's not very elegant, but it will work[/QUOTE]

Is that worth my time?  I mean, how much work would that require, and what would I have to do?

---

### Post by emerick7 on 2005-12-22
Found a way to get around it so that the screensaver will not activate during totem playback...

1. Download "brightside" from Synaptic
2. Go to System > Preferences > Screen Actions
3. Check one of the boxes depending on where you want it to "Prevent screensaver starting"
4. Next time you don't want your screensaver to activate (while watching a movie, playing music w/cool visualizations, etc.), just move your cursor to where you designated, and then no screensaver!

---

### Post by khc on 2005-12-24
[QUOTE=emerick7]Is that worth my time?  I mean, how much work would that require, and what would I have to do?[/QUOTE]

It should be something like this (note that I have not tested this):

xscreensaver-command -exit
totem $@
xscreensaver &

---

### Post by emerick7 on 2005-12-25
Just type those lines in a terminal?? Do I have to replace the $@ with anything, or just keep it as is?

---

