---
title: "Xine dvd play problem after upgrade"
date: 2005-04-06
forum: Desktop Environments
---

### Post by wxm505 on 2005-04-06
I upgrade My Ubuntu from Warty to Hoary.
After that xine desn't work well.
When I try it to play a dvd it pop up 2 error messages
like this:
First one:
There is no input plugin avaliable to handle 'dvd:/' Maybe
MRL sytax is wrong or file/stream source doesn't exist.

Second one:
The source can't be read.Maybe you don't have enough
rights for this, or source doesn't contain data(e.g: not disc in 
driver) (/dev/dvd)

The point is Totem works very well in the same case. And both
xine and totem worked pretty well before I updraded.

Any help guys?? cheers

---

### Post by bored2k on 2005-04-06
[QUOTE=wxm505]I upgrade My Ubuntu from Warty to Hoary.
After that xine desn't work well.
When I try it to play a dvd it pop up 2 error messages
like this:
First one:
There is no input plugin avaliable to handle 'dvd:/' Maybe
MRL sytax is wrong or file/stream source doesn't exist.

Second one:
The source can't be read.Maybe you don't have enough
rights for this, or source doesn't contain data(e.g: not disc in 
driver) (/dev/dvd)

The point is Totem works very well in the same case. And both
xine and totem worked pretty well before I updraded.

Any help guys?? cheers[/QUOTE]
 Do you have libdvdcss2? Have you tried MPlayer/VLC ?

---

### Post by wxm505 on 2005-04-06
Sure. I installed libdvdcss2 before I upgraded the box. It is still there.
I tried Mplayer. It can play but can not display the video only the sound.
Mplayer worked well under Fedora core 3 but does not work well
under Ubuntu at all. The error message said: It can not find CRT.
No idea what happened.
any idea??

---

### Post by wxm505 on 2005-04-07
Does anyone have any idea about this problem?
Cheers

---

### Post by bigzak on 2005-04-07
[QUOTE=wxm505]Does anyone have any idea about this problem?
Cheers[/QUOTE]

Try running Xine from the command line. It will dump far more useful messages to the console. Usually a message like you're getting indicates that it cannot find the DVD media, possibly because it is pointing at the wrong /dev/ entry.

---

### Post by wxm505 on 2005-04-07
It works well now . cheers mate

---

### Post by salah on 2005-04-07
I have problem with kaffeine when iuse the stream bottom it crashed any help?

---

### Post by Aidje on 2005-05-24
[QUOTE=wxm505]It works well now . cheers mate[/QUOTE]
 How did you solve the problem? I'm getting those same error messages, also after upgrading to Hoary.

edit: Never mind; I just had to change the DVD input device from /dev/dvd to /media/cdrom1

---

