---
title: "videos crashing Firefox"
date: 2005-12-15
forum: Desktop Environments
---

### Post by nix4me on 2005-12-15
Hi,

Every time I try to play the following videos in this order, my firefox (1.07 and 1.5) disappears.

To clarify, I am using mplayer, mplayerplug-in and w32codecs.
I have also tried it with totem and totem-xine.

The first video plays fine.  In fact I can play any mpg video no problem, but when i click on the second link, it doesnt play and firefox crashes.  I have tried many videos and it seems certain wmv always do this.

Here are the videos:
[ftp://ftp.motorcycle.com/pub/videos/Rolling_Burnout.mpg](ftp://ftp.motorcycle.com/pub/videos/Rolling_Burnout.mpg)
[http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv](http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv)

Is this a Firefox bug?
ps - The video plays fine in epiphany.

nix4me

---

### Post by jdong on 2005-12-15
mplayerplugin works here on both videos.

Can you start Firefox from a terminal, and paste any error output you get upon crash?

---

### Post by nix4me on 2005-12-15
/opt/firefox/run-mozilla.sh: line 131:  2517 Segmentation fault      "$prog" ${1+"$@"}


nix4me

---

### Post by nix4me on 2005-12-15
Also jdong, i talked with the developer of mplayerplug-in and he said the second link I posted should not play at all in mplayerplug-in.

I have confirmed this using epiphany.  It opens totem.

nix4me

---

### Post by art on 2005-12-15
I had a similar problem, so what I did was to follow this link

[http://ubuntuforums.org/showthread.php?t=76946&highlight=remove+totem](http://ubuntuforums.org/showthread.php?t=76946&highlight=remove+totem)

and now it does not crush.

---

### Post by nix4me on 2005-12-15
Well it seems that no wmv files are playing in mplayerplug-in.  How can I change this?

When i click a wmv, it trys to open an external player.  the only plugins in my plugins dir are the mplayer ones.

nix4me

---

### Post by nix4me on 2005-12-15
Ok.  I just talked to Kevin, the plugin developer.  He says that second video i posted above will not play in mplayerplug-in.  The reason is the mime type is wrong on the server.  The server sends the mime type txt/plain and therefore Mozilla can't figure it out.

I have tried properly set up wmv's and they work fine.

Now the real problem is, Firefox should not crash when an improper mime/type is detected.

I will file a bug with Firefox.

nix4me

---

