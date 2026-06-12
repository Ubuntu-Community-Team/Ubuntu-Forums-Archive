---
title: "Can't play mp3-files"
date: 2005-08-22
forum: Desktop Environments
---

### Post by MdaG on 2005-08-22
I've tried installing xmms and zinf, but I can't get neither to actually play anything. I know my soundcard works since I get sound through gnome and gaim... What n00b mistake have I done?

---

### Post by mcmuffy on 2005-08-22
List of HOWTO's

[http://www.ubuntuforums.org/showthread.php?t=53050&highlight=howto+mp3](http://www.ubuntuforums.org/showthread.php?t=53050&highlight=howto+mp3)

---

### Post by MdaG on 2005-08-22
[QUOTE=mcmuffy]List of HOWTO's

[http://www.ubuntuforums.org/showthread.php?t=53050&highlight=howto+mp3](http://www.ubuntuforums.org/showthread.php?t=53050&highlight=howto+mp3)[/QUOTE]

Are you reffering to the sound daemons? I don't think that's the problem. If so Gaim shouldn't be working. XMMS actually freezes when I try to play music through it...

*edit*
Is there any official documentation for Ubuntu?

---

### Post by Tuxhedoh on 2005-08-22
I'm glad you asked about this. XMMS locks up on me too. I haven't searched the forum yet about this issue. Now that this is at the top, maybe I won't have to.

---

### Post by MdaG on 2005-08-22
Am I suppose to configure alsa manually? If so, how? The HOWTO guide doesn't have answers to my problem. I've edited esd so that it's not used when it's not needed. I ask again: Is there an official documentation for Ubuntu similar to [this](http://www.gentoo.org/doc/en/list.xml)?

---

### Post by chrisod on 2005-08-22
Ubuntuguide.org and the wiki are about as official as it gets. However, I've yet to have a problem that I couldn't solve with those two sources.

---

### Post by MdaG on 2005-08-22
Thanks, this [url=https://wiki.ubuntu.com/UserDocumentation
]wiki[/url] solved my sound problem!  :grin: 
The problem is that ALSA sink isn't deafult in Ubuntu. All i needed to do was follow this [guide](https://wiki.ubuntu.com/SoundProblemsHoary). Thanks for the help guys, I still have some stuff to do (like configure Java), but that's another thread...

*edit*
Oh, and I'm using beep-media-player just in case anyone wonders...

---

