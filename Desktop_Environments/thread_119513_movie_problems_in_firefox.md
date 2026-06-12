---
title: "movie problems in firefox"
date: 2006-01-19
forum: Desktop Environments
---

### Post by baldy1324 on 2006-01-19
i cannot get any kind of media working in firefox-i can get flash stuff working but real video formats (mpeg, mov, wmv, ...) wont work. in about: plugins-it clearly shows all of these files associated with the right plugins. i have tried using the vlc plugin, mozplugger (which only plays audio, no video), mplayer-plugin, totem-xine-firefox, and totem-gstreamer-firefox. they all show there connections with the media types in about:plugins.
:confused:

---

### Post by matthewv on 2006-01-19
Do you have all the codecs installed. By default ubuntu will not play proprietary formats like mp3, wma, wmv, quicktime etc. See [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) for more info

---

### Post by bikeman on 2006-01-19
Automatix is a really slick, wonderful script that may make your life much easier.  It worked perfectly for me for those options I selected (note: read the warnings about legal stuff depending on where you live).  Just make sure that you have sudo set up correctly (I didn't, once I added myself to the sudoer list all went well).  Go to [this]("http://www.ubuntuforums.org/showthread.php?t=80295&highlight=Automatix") thread for information.  Hope that helps.

---

### Post by melissawm on 2006-02-16
I have the same problems, all the codecs, automatix didn't fix it. I've tried ALL types of player/plugins without success.. This is really putting me off the whole ubuntu experience since currently I have no TV and my only chance to watch some news and stuff is through the internet, and I end up using windows, which i really only use if strictly necessary... can someone please help us?? Arnieboy, if you're out there, could you point some reason why automatix didn't work for me? I admit I had already tried other stuff before I used automatix, is it necessary that I uninstall everything I had tried first (manual plugin installation, etc) in order for automatix to work?

Please, help!!!

Just before I forget, all files play off the web, in all the players. It's just the streaming videos through firefox that don't work. I also already tried mediaplayerconnectivity, and i don't even see the black square with the little buttons...

---

### Post by nalmeth on 2006-02-16
can you post some sites that you are trying to stream video from (safe for all eyes ;) ) My mozplugger works quite well from automatix. Are you using firefox 1.5? dunno if this is a factor, probably not :-k

---

### Post by melissawm on 2006-02-16
The thing is that the site i'm trying to play has a password, i don't know if that's the problem but indeed it doesn't play. I've uninstalled and installed firefox and all the other multimedia players/codecs/plugins today, and now they do seem to work, but not this specific site (which murphycally, is the only one i'm really interested in playing). Are there some other brazilian users who try to play GloboNews from inside the Globo Media Center? If someone has managed to do it, please let me know..

p.s. mplayer freezes completely when i try to play anything, i'm currently using xine, which is the only one that seems to work...

---

### Post by melissawm on 2006-03-26
Ok just to be clear here. I found another question similar to my own question and the solution is to install all the plugins with firefox CLOSED. It seems really stupid, but i'm wondering how come you don't get an error message if keeping firefox open is such an issue...

Anyway, if you install all the plugins etc with you firefox closed, it works. At least for me, it did.

---

### Post by gpeck157 on 2006-04-20
[QUOTE=melissawm]I have the same problems, all the codecs, automatix didn't fix it. I've tried ALL types of player/plugins without success.. This is really putting me off the whole ubuntu experience since currently I have no TV and my only chance to watch some news and stuff is through the internet, and I end up using windows, which i really only use if strictly necessary... can someone please help us?? Arnieboy, if you're out there, could you point some reason why automatix didn't work for me? I admit I had already tried other stuff before I used automatix, is it necessary that I uninstall everything I had tried first (manual plugin installation, etc) in order for automatix to work?

Please, help!!!

Just before I forget, all files play off the web, in all the players. It's just the streaming videos through firefox that don't work. I also already tried mediaplayerconnectivity, and i don't even see the black square with the little buttons...[/QUOTE]

Try this if you haven' already. It worked for me.
```
sudo apt-get install mplayer-386
sudo apt-get install mplayer-fonts
sudo apt-get install mozilla-mplayer
```
G

---

