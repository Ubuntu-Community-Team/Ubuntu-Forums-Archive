---
title: "Xubuntu (Edgy) Compose Keys"
date: 2006-11-09
forum: Desktop Environments
---

### Post by casperl on 2006-11-09
Hi all,

I did a clean install of Xubuntu Edgy.  In Ubuntu Dapper and Breezy I could go to System, Preferences, Keyboard > Layout Options, > Compose key position > Choose Right-Win key is compose

That allowed me to enter special characters in German, Dutch and Afrikaans using a three character sequence on the keyboard.

Call me an idiot :-k (and you may be right), but I have searched high and low for this functionality in Xubuntu ](*,) 

Does anyone know where?  How?  :confused:

---

### Post by nekr0z on 2006-11-16
There's no such functionality in XFCE, so you have to set it up in X.org. This is done by adding a line in /etc/X11/xorg.conf
```
 Option   "XkbOptions"   "compose:caps"
```
This should be added into "InputDevice" section that deals with keyboard.

After editing xorg.conf you are to restart X for the changes to take effect.

---

### Post by casperl on 2007-03-02
No, the above in /etc/X11/xorg.conf did not work.  It is many months since the original post and I have struggled along, but now this functionalitiy of being able to enter extended characters in xubuntu is  becoming critical.

According to the above info, this is my present xorg.conf:

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbOptions"   "compose:caps"
EndSection

Certainly to date I am unable to enter extended characters (other than with the Character Map apps) from the keyboard.  Are there any other wans that will work?

---

### Post by MysticAurora on 2007-03-30
> **nekr0z said:**
> There's no such functionality in XFCE, so you have to set it up in X.org. This is done by adding a line in /etc/X11/xorg.conf
```
 Option   "XkbOptions"   "compose:caps"
```
This should be added into "InputDevice" section that deals with keyboard.

After editing xorg.conf you are to restart X for the changes to take effect.

Thanks a lot, that worked! However, how can I make it to where Caps Lock doesn't seem to toggle, or better yet, assign Compose to right Alt?

---

### Post by nekr0z on 2007-03-30
Compose key works like that: you press Compose, release it, then press a key you need, release it, then press another one, and so it goes until you've entered the whole sequence. After you did, the keyboard automatically goes back into normal mode, and you go on printing. This system ensures you can use sequences like "Compose, a, a" (that makes "å"). So there's absolutely no point in switching what you called "toggle" off, and I seriously doubt this is implemented at all.

You can use other keys for Compose, just put ralt, rwin, lwin or others — whatever you see fit — instead of caps.

Casperl, it's 4 weeks after you posted, so I'm sure you have already managed to make things work, but just in case you haven't: your InputDevice section has two XkbOptions lines, which makes the second one to be ignored. What you need to do is put both in one line, like```
Option   "XkbOptions"   "lv3:ralt_switch,compose:caps"
```

---

### Post by holomorph on 2007-04-24
where can I find some documentation on the options that can be used with "XkbOptions"?  I've been digging around man pages but obviously not the right ones :(

---

