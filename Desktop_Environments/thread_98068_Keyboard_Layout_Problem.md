---
title: "Keyboard Layout Problem"
date: 2005-12-02
forum: Desktop Environments
---

### Post by golyat on 2005-12-02
My keyboard layout is Turkish Q. I have tested it in pre-installation stage, it works. But when finished installing Ubuntu it didn't work ( I mean some of characters ) and I couldn't change the layout from Keyboard Layout Selector it gives error. Can you help me about this?

---

### Post by 23meg on 2005-12-02
In Applications / System Tools / Configuration Editor, go to /desktop/gnome/peripherals/keyboard/kbd/ and enter "tr" into "layouts" and "pc105" into "model", without the quotes.

Also make sure the InputDevice section of your xorg.conf file corresponding to your keyboard looks like this: ```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
	Option		"XkbVariant"	"q"
EndSection
```

---

### Post by meborc on 2005-12-02
ok... this problem has been up before... and if you search the forum you could find different solutions, but this is what i did, to solve the problem: 

first type into terminal:
```
sudo gedit /etc/X11/xorg.conf
```

then edit the file part shown below:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"**[COLOR="DarkRed"]pc105[/COLOR]**"
	Option		"XkbLayout"	"**[COLOR="DarkRed"]ee[/COLOR]**"
EndSection
```
where the **[COLOR="DarkRed"]pc105[/COLOR]** is the number of keys on the keyboard (mine 105 as you see) and the **[COLOR="DarkRed"]ee[/COLOR]** stands for the layout name (mine is ee - estonian)

hope that helped a bit... but try the search, the keyboard/layout problem is well known!


EDIT: da*n 23meg - you are quick :) ... sorry for doublepost...

---

### Post by meborc on 2005-12-02
oh, a quick question, what does line ```
Option		"XkbVariant"	"q"
``` stand for? :(

---

### Post by 23meg on 2005-12-02
It's the keyboard type; "q" being a QWERTY keyboard and "f" being an F one.

---

### Post by teaker1s on 2005-12-02
it's a gnome/xkb problem look [here]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/2963")

---

### Post by meborc on 2005-12-02
[QUOTE=23meg]It's the keyboard type; "q" being a QWERTY keyboard and "f" being an F one.[/QUOTE]
ok, i see... and if i don't have this line? does it automatically assume i use q?

---

### Post by 23meg on 2005-12-02
Not sure but if you don't have any problems at present, leave it as is.

---

### Post by teaker1s on 2005-12-02
my keyboard was set as gb in xorg config but it was screwed up in gnome if your region is missing then keyboard will behave oddly in gnome

---

### Post by golyat on 2005-12-02
Thank you all.

---

### Post by baytuni on 2006-01-27
i did all of these but still it doesn't respond to turkish letters and alt keys. What else i can do?

---

