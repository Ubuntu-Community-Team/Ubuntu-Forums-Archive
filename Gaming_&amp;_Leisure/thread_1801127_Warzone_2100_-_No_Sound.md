---
title: "Warzone 2100 - No Sound"
date: 2011-07-09
forum: Gaming &amp; Leisure
---

### Post by MelissaCutler on 2011-07-09
Hiya,

I also have no sound when I try to play Warzone2100.  Everything else in the game seems to work fine.  And sound works in other programs.

The game used to work perfectly (including sound) but then I stopped playing for a while.  Now I have gone back to it and it is silent - voice, sfx or music.  I have no idea why, they only thing that seems to have changed since before is the automatic update of Ubuntu.

I have checked and PulseAudio ESD compatibility layer is already installed on my system.

There is another thing that puzzels me about warzone, and full screen applications in general; it seems to dissable all of my keyboard shortcuts, so that there is no way to minimise it and access my Gnome applets while it is running.  I mention this because usually when I have no sound in a program, I look at the sound applet and often that program has been muted there and needs it's volume turned back up.  But with war-zone I can't see of access the sound applet.

Help would be greatly appreciated.  When replying please remember that I am a total beginner who is very easily confused by Linux.

Thank you,

Melissa

---

### Post by MelissaCutler on 2011-07-09
Update:

I found a post on a forum for Warzone where someone described a similar problem.

[http://forums.wz2100.net/viewtopic.php?t=4615](http://forums.wz2100.net/viewtopic.php?t=4615)

Someone said that it could be fixed by changing a line in the file: /etc/openal/alsoft.conf
I found a line relating to drivers and changed it to:
drivers = oss,alsa,pulse

I had to open the location in a terminal, and use:
sudo gedit alsoft.conf
before my text editor was able to save in that location.

I don't really understand any of this, but it is working now, and I thought I'd mention what I have done in case this is helpful to others.

Cheers,

Melissa

---

