---
title: "minimize to tray"
date: 2005-05-22
forum: Desktop Environments
---

### Post by sapo on 2005-05-22
Is there a way to minimize xmms to the tray instead of the taskbar?

I leave my xmms open 24/7 and it is always taking some precious space in my taskbar.. i would like to put xmms on the tray like gaim.. and azureus.

Is there some kind of plugin or somethink like it?

Thanx  \\:D/

---

### Post by NeoChaosX on 2005-05-22
There's a plugin to put an XMMS icon in the tray. It doesn't get rid of the taskbar button, though.

---

### Post by bored2k on 2005-05-22
[http://www.sosdg.org/~larne/w/Plugin_list](http://www.sosdg.org/~larne/w/Plugin_list)
XMMS Scrobbler / BMP Scrobbler

It removes the xmms/bmp completely from the taskbar. I've tested this on bmp..

---

### Post by sapo on 2005-05-23
[QUOTE=bored2k][http://www.sosdg.org/~larne/w/Plugin_list](http://www.sosdg.org/~larne/w/Plugin_list)
XMMS Scrobbler / BMP Scrobbler

It removes the xmms/bmp completely from the taskbar. I've tested this on bmp..[/QUOTE]


I ve tried to install it but i got a lot of erros in the configure script

isnt there some pre-compiled stuff or a .deb file?

thanx  ](*,)

---

### Post by bassMonkey on 2005-05-23
You could always try kdocker, works pretty good and docks about any app you can think of. Currently I have thunderbird, beep-media-player and gimp docked... :smile:

---

### Post by jebe on 2005-05-30
hi,

maybe my program alltray is what you looking for

[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

version > 0.51 have special xmms support (i suggest using latest dev release)


jebe

---

### Post by bored2k on 2005-05-30
[QUOTE=sapo]I ve tried to install it but i got a lot of erros in the configure script

isnt there some pre-compiled stuff or a .deb file?

thanx  ](*,)[/QUOTE]
 What are the errors ? I could help you there.

Install this 
beep-media-player-dev (or xmms-dev) libmusicbrainz4-dev build-essential then try ./configure then make then sudo make install

[IMG]http://img42.echo.cx/img42/7190/love9bt.png[/IMG]

---

### Post by kxs on 2005-07-06
[QUOTE=jebe]hi,

maybe my program alltray is what you looking for

[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

version > 0.51 have special xmms support (i suggest using latest dev release)


jebe[/QUOTE]

really nice!  :)

edit: hmm..   :???: but there`s a little problem with the play list. it disappears. what can I do about it?

---

### Post by jebe on 2005-07-06
hi,

what do you mean exactly ? or what do you expect ?

the playlist disappear when the main window disappear. 

jebe

---

### Post by kxs on 2005-07-07
I mean that it disappears from XMMS. I can`t turn it on with the playlist button. When I use XMMS without AllTray it`s all OK. I can turn playlist on and off with no problems. But when I run 'alltray xmms' the playlist`s gone. 
I`ve managed to turn it on starting pure xmms, turning off playlist, closeing xmms and starting alltray xmms. Then, when I use the playlist switch, the playlist appears, but after hiding xmms on tray and getting it back the playlist is gone for good again.

---

### Post by jebe on 2005-07-07
[QUOTE=kxs]I mean that it disappears from XMMS. I can`t turn it on with the playlist button. When I use XMMS without AllTray it`s all OK. I can turn playlist on and off with no problems. But when I run 'alltray xmms' the playlist`s gone. 
I`ve managed to turn it on starting pure xmms, turning off playlist, closeing xmms and starting alltray xmms. Then, when I use the playlist switch, the playlist appears, but after hiding xmms on tray and getting it back the playlist is gone for good again.[/QUOTE]

mmh can not reproduce this bug. works fine here. but somebody else have the same probs...

please send the output from "xprop" (point with the cursor on the playlist window)
to email at jochen-baier.de

thanks

---

### Post by Daicogra on 2005-07-11
You can compile it with "Koniu's patch". Then you don't have it in the taskbar.

[http://www.sosdg.org/~larne/w/Resources](http://www.sosdg.org/~larne/w/Resources)

---

### Post by zeuz on 2005-08-09
Jebe: No playlist for me either, need any information?

---

### Post by RastaMahata on 2005-08-26
made a very rough deb package of bmp-docklet 1.3.

---

### Post by nozey on 2005-08-26
Here u can learn how to put xmms on tray:

[http://www.ubuntuforums.org/showthread.php?t=21789](http://www.ubuntuforums.org/showthread.php?t=21789)

---

