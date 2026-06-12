---
title: "totem decoder-codecs"
date: 2006-09-26
forum: Desktop Environments
---

### Post by IusedTObeSOMEONEelse on 2006-09-26
totem says I need decoder/codecs. where and wich ones do I need? Thanks

---

### Post by Kateikyoushi on 2006-09-26
It depends on what do you want to play.

Most likely you have to add new repositories, use synaptic for that.

[Link.]("http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29")

Then copy to terminal.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```

This should be enough for most videos audios.

---

### Post by IusedTObeSOMEONEelse on 2006-09-26
will that work for edgy asa that's what I'm using

---

### Post by Kateikyoushi on 2006-09-26
I am also using edgy and alsa and works for me.

---

### Post by IusedTObeSOMEONEelse on 2006-09-26
:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-gl is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by croak77 on 2006-09-26
What type of file are you trying to play?

---

### Post by calisun on 2006-12-14
I have the same problem when trying to run above mentioned command. I also keep getting same massge that totem is missing a decoder. I get this message all the time when I try to play any kind of file: mp3, mpg, avi... anything, I was never able to play anything on totem player.

---

### Post by ferald on 2007-01-11
You need to install some extra Codecs to get Totem to play most format.
I use Gstreamer with Totem and with correct codec install it worked great, worked with Rhythmbox too.


Multimedia Codecs: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html")
Check here aswell for more: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Official Desktop Guide: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html")

---

