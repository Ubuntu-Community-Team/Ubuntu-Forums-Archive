---
title: "Serial Mouse problems ... still ..."
date: 2005-12-02
forum: Desktop Environments
---

### Post by imstarlost on 2005-12-02
Trying to use Breezy Badger live prior to actually installing it. Everything seems to load OK, but the mouse cursor looks so pretty just sitting in the middle of the screen ... no action.

Tried to follow the SerialMouseHowto specified for 5.04, but I get no selection to specify the mouse port or to inform it of MS compatibility. 

So ...  how do I get around this problem with Breezy Badger?

TIA

Kenny

---

### Post by teaker1s on 2005-12-02
look [here]("http://ubuntuforums.org/showthread.php?t=65471") it should show you how to get the info you need for xorg.conf
yes I know its a usb mouse but it will get you on the right track

---

### Post by pakux on 2005-12-04
did you try to change your /etc/X11/xorg.conf ?

the "simple" way to change your mouse/keyb/display settings if you're too afraid of messing up your system (as all we n00b's are) is using sudo dpkg-reconfigure xserver-xorg (maybe you want also to keep a backup copy first) and accept all current settings but one at a time.

however, the simplest way is editing the configuration file as described in this thread:
[http://ubuntuforums.org/showthread.php?t=96635&highlight=serial+mouse+xorg.conf]("http://ubuntuforums.org/showthread.php?t=96635&highlight=serial+mouse+xorg.conf")

in these days i'm configuring and old desktop, the serial mouse refuse to be recognised and the suggested method worked fine (all thanks to Aragorn2929).

hope it helps.

---

