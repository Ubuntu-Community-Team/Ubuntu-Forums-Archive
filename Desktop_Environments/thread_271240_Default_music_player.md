---
title: "Default music player"
date: 2006-10-04
forum: Desktop Environments
---

### Post by zell77 on 2006-10-04
i have this problem

from System-->Shortcuts keyboard

i can set every key of my keyboard (like play, stop, pause, open default player...)

default player is Rhythmbox

but if i want that default player is XMMS, how can i do?

i try to change /usr/share/applications/defaults.list 
i change rhythmbox with xmms but nothing...

someone can help me?

Daniele

ps. sorry for my english...

---

### Post by zell77 on 2006-10-04
nothing? :(

---

### Post by aidanr on 2006-10-04
rename /usr/bin/rhytmbox to /usr/bin/rythmbox.old 
and then copy /usr/bin/xmms to /usr/bin/rhytmbox

works for me with sonata

---

### Post by zell77 on 2006-10-04
yes now if i try to open default player there is xmms

but the shortcuts to manage player doesn't work..(play, stop, etc..)

another help?

Thanks for answer

---

### Post by aidanr on 2006-10-04
try krackers suggestion here
[http://www.ubuntuforums.org/showthread.php?p=440027#post440027](http://www.ubuntuforums.org/showthread.php?p=440027#post440027)

---

### Post by zell77 on 2006-10-04
i try...but nothing

i install xbindkeys-config
i create file ~/.xbindkeysrc, i put in:

(xbindkey '(XF86AudioPlay) "xmms --play-pause")
(xbindkey '(Mod4 x) "xmms --play-pause")

(xbindkey '(XF86AudioPrev) "xmms --rew")
(xbindkey '(Mod4 Left) "xmms --rew")

(xbindkey '(XF86AudioNext) "xmms --fwd")
(xbindkey '(Mod4 Right) "xmms --fwd")

(xbindkey '(XF86AudioStop) "xmms --stop")

and i run xbindkey

but doesn't work

---

### Post by aidanr on 2006-10-04
right, install xbindkeys, i think xbindkeys and xbindkeys-config are different packages? (at work here on windows so can't check it out)

where he has XF86AudioPrev,Mod4 x etc will probably be different to you, so you can find out the proper key codes by running xev in a terminal and then pressing the media keys

hope that makes sense

---

### Post by zell77 on 2006-10-04
thanks now it works ok

thanks a lot!!!

---

### Post by aidanr on 2006-10-04
great, no problem:)

---

