---
title: "Changing Default Media Players"
date: 2006-07-19
forum: Desktop Environments
---

### Post by asplode on 2006-07-19
Just a quick question...

How does one go about changing the default media player applications?

Dapper seems to default MP3 files to Totem, instead of something awesome like banshee or even rhythmbox, a real MP3 player...

Also, how would one go about changing the default video player from totem to something more reliable, like gxine or mplayer?

I compiled the latest totem (1.5.4) and it still seems to be unstable.  Fastforwarding in totem gives me internal data flow errors... Friggin totem.

---

### Post by llamakc on 2006-07-19
From the Gnome menu:

System > Preferences > Removable Drives and Media > Multimedia

---

### Post by asplode on 2006-07-19
I've seen that before, but that only seems to work for DVDs, Ipods, and audio cds...  Not necessarily MP3 and video files.

---

### Post by asplode on 2006-07-19
I thought there was some sort of CLI command such as

sudo update-alternatives *something*

---

### Post by llamakc on 2006-07-19
Yikes, you're right. Sorry.

In gconf-editor you can set something at desktop > gnome > url-handlers > mms

and other spots in there.

---

### Post by llamakc on 2006-07-19
Yep,

sudo update-alternatives --list (or --config) "name of symlink in /etc/alternatives"

though I don't see anything at first look.

---

### Post by asplode on 2006-07-19
Whoa... gconf-editor... never seen this before... I'll have to poke around in it...

---

