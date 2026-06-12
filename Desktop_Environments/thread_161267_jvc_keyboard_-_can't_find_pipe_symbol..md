---
title: "jvc keyboard - can't find pipe symbol."
date: 2006-04-16
forum: Desktop Environments
---

### Post by dotdot on 2006-04-16
hi folks - ok an obscure question i know .. but here goes.

today installed ubu 510 onto a monster of a mini laptop..
it'sa mp-xp7310 subnotebook.

only problem is it has a japanese keyboard... and i cant for the life of me find the pipe symbol - something i can't really do without.

i'm configed using uk uk keyboard...

anyone have any ideas.. ?

tia..

---

### Post by Zimmer on 2006-04-17
An obvious guess:
hold down shift (LH side of keyboard) and the press the key to the right of it.
Or Shift plus whatever is the first proper key on the left of the row above the space bar...

Otherwise you could try playing with the input methods in Terminal (right click in Terminal for a menu)

---

### Post by Titus A Duxass on 2006-04-17
I have a German version of this mini-book, the 3210DE and on my keyboard (German) the pipe is the key to the right hand side of the left hand shift key and requires AltGr + the pipe key.

The AltGr is the key to the right hand side of the space bar. I cannot remember what this is on an English keyboard.

Incidentally, how did the installation go, where there any problems.  Mine is running XP at this moment but I want to do the ubuntu thing on it.

---

### Post by dotdot on 2006-04-19
still no joy people.

It would appear i have a few keys which simply do 
not output anything at all.

..and the pipe key is one of them.

if i go into keyboard shortcuts pick and object to change 
then select the pipe key  - i get no response echoed to screen.

otherwse = the install went smoother than i could have 
expected.... it found absolutely everything including wireless.

any further ideas people ? would be much appreciated.

..

---

### Post by Zimmer on 2006-04-19
Clutching at straws, but what does your xorg.conf show for keyboard?
Mine shows this, if that's of any use..
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

---

### Post by dotdot on 2006-04-19
sorry - i'm having problems with finding pipe and assoc cmd lines....
where should i find this config. ? .... i think cut and paste should work fine....

...I've contacted jvc on this btw - getting spookier by 
the minute -  this problem...

thanks for all the suggestion so far...

---

### Post by dotdot on 2006-04-19
found the file...

info as requested...

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

---

### Post by Zimmer on 2006-04-19
No surprises there, then..I thought there might have been a dodgy entry that could have accounted for the problem..

---

### Post by fonggiding on 2006-04-27
I use a Japanese 106 keyboard and I got the same problem when I switched to dvorak three hours ago. Go dvorak:KS !!! I couldn't use | and "hankaku zenkaku". I solved it by re-mapping the useless keys by

```
xmodmap -pke > Xmodmap.dvorakjp
```

Then I found the | key which happened to be keycode 133 and I added:
backslash bar prolongedsound
in 49 (hankaku zenkaku) I added:
Zenkaku_Hankaku Kanji

Then to finish up I ran
```
xmodmap Xmodmap.dvorakjp
```

This is my /etc/xorg.conf:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"jp106"
	Option		"XkbLayout"	"jp"
	Option		"XkbVariant"	"jp106"

Good Luck!

---

### Post by dotdot on 2006-04-30
thanks for the ideas.. i've only just spotted your post - will attempt fix once i get out of the current [hole]("http://ubuntuforums.org/showthread.php?t=168447") in i'm in..



..

---

### Post by dotdot on 2006-05-13
thanks ... i did the xmodmap mod and lo and behold it's all now working fine ...

 :) || <<--

..what with dapper upgrade now this - we're cooking !

..

---

