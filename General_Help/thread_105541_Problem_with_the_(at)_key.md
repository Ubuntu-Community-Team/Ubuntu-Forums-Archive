---
title: "Problem with the (at) key"
date: 2005-12-18
forum: General Help
---

### Post by thranduil on 2005-12-18
hi guys.

i instaled ubunto 5.1 yesterday and i am trying to make a "2nd first step" into linux :P 

my problem is that i am from portugal and i use a portuguese keyboard. i have no problems with chars like ã or é. my onlye problem with chars is the (at) key, the (euro) key and all those third-keys. 
i hope anyone can help me. i really need to configure this so i can use email and chats decently.
thanks

---

### Post by endersshadow on 2005-12-18
Go to System>Preferences>Keyboard

Go over to the Layout Options Tab

Select Third Level choosers, and select which one you'd like to use.

You should be all set :-D

---

### Post by rcerreto on 2005-12-18
That's strange, once you choose a Portuguese layout for your keyboard, @ and € should be available. I'm using an Italian one with no problems.

Anyway, assuming you're using gnome:
System -> Preferences -> Keyboard

select the "Layout Options" tab

there you'll find many helpful options

---

### Post by thranduil on 2005-12-18
hmmm i have already tryed that...

[[IMG]http://show.imagehosting.us/show/1011677/0/nouser_1011/T1_-1_1011677.png[/IMG]](http://www.imagehosting.us/index.php?action=show&ident=1011677)

those errors appear everytime I change anything in that menu... 

but thanks, anyway :P

---

### Post by endersshadow on 2005-12-18
I can't read Portugese :-|

---

### Post by thranduil on 2005-12-18
oh f***

i'm really sorry!!!

here is the translation of the two error windows:
1. Error activating XKB configuration.
It may happen in various circumstances:
- an error in the libxklavier library
- an error in the X server (xkbcomp, xmodmap utils.)
- X server with an incompatible implementation of the libxkbfile library

Data of the X server version:
The X.Org Fountation
60802000

If you mention this situation as an error (in english), include:
- the result of xprop -root | grep XKB
- the result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


2. equal to the first.


results of:
**xprop -root | grep XKB**
> thranduil@joao:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "pt", "pt", "pt"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "pt", "pt", "pt"


**gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd**
> thranduil@joao:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [pt  pt]
 model =
 options = [grp grp:alts_toggle,eurosign        eurosign:e,lv3  lv3:lalt_switch] overrideSettings = true


i hope you understand this now :P
and sorry my 14yo english :P but i guess in this text there are no errors. ^^

---

### Post by thranduil on 2005-12-19
i may add that this error appears everytime i login in to the system...

---

### Post by rcerreto on 2005-12-19
I'm sorry but nothing smart comes to my mind.
It looks like something is broken in your Xserver config but I can't say what.
Maybe that installing using an English keyboard and then adding a Portuguese one will fix the issue. Not sure at all though.

---

### Post by KrIaXPaTaLa on 2006-03-25
Hey there.

I was having the same problem (pt keyboard as well), and it seems it was a stupid bug, since it didn't work with the portuguese layout alone, I had to reset to default (english keyboard) and then I added the portuguese, keeping the english. It works fine, now.

Running dapper here.

Regards,

KrIaX, Portugal.

---

