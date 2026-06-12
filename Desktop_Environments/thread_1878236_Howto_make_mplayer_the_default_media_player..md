---
title: "Howto make mplayer the default media player."
date: 2011-11-09
forum: Desktop Environments
---

### Post by eddie70 on 2011-11-09
Hi All 

This is a new UBUNTU 11.10 install

I am just about ripping all my hair out trying to figure out how to get mplayer (and more to the point mplayer no gui) as my default media player.

I have uninstalled banshee and totem and now I just get error messages when I try and open media such as avi or mpg. It does not give me any options to try and enter my own chooses. 

The options I am getting in unity and gnome both classic and the new one are:
Show other applications or find applications on line.  None of which are what I want or any use at all.

How do I get the old functionality back where I can enter A path to the binary that I want to handle the object that i want to open ?

Thanks 
Getting mighty frustrated with the new desktop environments.

---

### Post by Bonster on 2011-11-09
right click on the file like avi > properties > open with
then add in mplayer

---

### Post by eddie70 on 2011-11-17
Hi 

Thanks for replying 

I tried this and all I get is the same options that I got from left click > openwith. Namely a list off programs (without mplayer) and a select from the internet.  

The was no option to enter a path to an application.

---

### Post by mswift on 2011-11-17
You need to make a mplayer.desktop file:

```
cd && cd /usr/share/applications
```
```
sudo gedit mplayer.desktop
```
and paste this:

```
[Desktop Entry]
Version=1.0
Name=Mplayer media player
GenericName=Media player
Comment=Read, capture, broadcast your multimedia streams
Exec=mplayer %U
TryExec=mplayer
Icon=mplayer
Terminal=false
Type=Application
Categories=AudioVideo;Player;
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;application/ogg;application/x-ogg;video/x-ogm+ogg;audio/x-vorbis+ogg;application/x-matroska;audio/x-matroska;video/x-matroska;video/webm;audio/webm;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-mpegurl;audio/x-scpls;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;video/vnd.rn-realvideo;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;video/mp4;video/mp4v-es;x-content/video-vcd;x-content/video-svcd;x-content/video-dvd;x-content/audio-cdda;x-content/audio-player;video/x-flv;application/xspf+xml;
X-KDE-Protocols=ftp,http,https,mms,rtmp,rtsp,sftp,smb
```

Save the file and you will be able to select mplayer as an alternative video-player.

---

