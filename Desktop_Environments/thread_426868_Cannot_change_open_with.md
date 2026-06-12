---
title: "Cannot change open with"
date: 2007-04-28
forum: Desktop Environments
---

### Post by katzman on 2007-04-28
hi all;
got my F.Fawn install up ad running nicely except for one thing
in Nautilus if I try to change the default programm for say movies, on the Properties dialog it will not let me.
I can click on say VLC and the raio button deos not move, nor does it get changed anyway

Anyone have any thoughts?

---

### Post by ComplexNumber on 2007-04-29
> **katzman said:**
> hi all;
got my F.Fawn install up ad running nicely except for one thing
in Nautilus if I try to change the default programm for say movies, on the Properties dialog it will not let me.
I can click on say VLC and the raio button deos not move, nor does it get changed anyway

Anyone have any thoughts?
what you need to do is to go to /usr/share/applications in the terminal and open up the vlc file as root. you will see the following below, and the mime type is what you want to change. the reason it doesn't let you change it is because almost everythign outside of your home directory is owned by root, and the vlc entry is owned by root. therefore, you, as a non-privileged user, will not be able to change it. you can only change entires that you've added yourself.
```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.2
Name=VLC media player
Name[fr]=lecteur multimédia VLC
Comment=Universal movies and music player
Comment[fr]=Lecteur universel pour films et musique
Exec=wxvlc
Icon=vlc
Terminal=false
Type=Application
Categories=Application;AudioVideo;Player;
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;application/ogg;application/x-ogg;application/x-matroska;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-mpegurl;audio/x-scpls;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;application/x-matroska;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;video/vnd.rn-realvideo;audio/x-pn-realaudio-plugin;

```

---

