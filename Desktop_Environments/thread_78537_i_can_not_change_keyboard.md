---
title: "i can not change keyboard"
date: 2005-10-18
forum: Desktop Environments
---

### Post by oldforce on 2005-10-18
when i try to change the keyboard layout it gives an eroor like this:
XKB yap&#305;land&#305;r&#305;lmas&#305; etkinle&#351;tirilirken hata.
Çe&#351;itli sebeplerden bu olu&#351;abilir:
- libxklavier kütüphanesindeki bir hatadan
- X sunucusundaki (xkbcomp, xmodmap araçlar&#305;) bir hatadan
- X sunucu ile uyumsuz libxkbfile uygulamas&#305;ndan

X sunucu sürümü bilgisi:
The X.Org Foundation
60802000

E&#287;er bu durumu bir hata olarak bildirirseniz, lütfen bunlar&#305; ekleyin:
- xprop -root | grep XKB sonucu
- gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd sonucu

it is in turkish
one more thing special turkish characters do not work on my keyboard with ubuntu 5.10

---

### Post by odin on 2005-10-19
umm...If you could translate the error message it would be easier to help you.....

---

### Post by oldforce on 2005-10-19
i see this error when gnome starts and i can not use special turkish characters like &#351;,ç,ü,ö and @.
if you browse with turkish page encoding you can see the letters..

translation of error:)

Error while activating XKB r&#305;lmas&#305;.
This should be caused by:
- an error in libxklavier library
- an error in X server (xkbcomp, xmodmap tools)
- aplied libxkbfile is incompatible with X server

X server version info:
The X.Org Foundation
60802000

- xprop -root | grep XKB hence
- gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd hence

---

### Post by neymac on 2005-10-20
[QUOTE=oldforce]i see this error when gnome starts and i can not use special turkish characters like &#351;,ç,ü,ö and @.
if you browse with turkish page encoding you can see the letters..

[/QUOTE]

I have the same problem in Brazilian Portuguese, and I've searched through others threads and discovered several messages with this problem in French, Spanish, Dutch, etc. I have Ubuntu 5.10 and 5.04 in the same computer, and in Hoary works well. In my install of Breezy everythig run well, but this small problem. Without doubt Breezy is better than Hoary, IMHO.

My keyboard is Microsoft Natural, and the Layout selected is English-US.

---

### Post by lonmyown on 2005-10-23
I have the same problem with my packard bell b3560 with turkish keyboard. Everythig works fine but the national characters...

does anybody have a solution? I really need to use ubuntu...

---

### Post by ozorba on 2005-10-24
[QUOTE=lonmyown]I have the same problem with my packard bell b3560 with turkish keyboard. Everythig works fine but the national characters...

does anybody have a solution? I really need to use ubuntu...[/QUOTE]

Try this:
1. sudo dpkg-reconfigure locales 
and select "tr_TR ISO-8859-9" and  "tr_TR.UTF-8 UTF-8" for turkish (for other languages select the associated ISO and UTF-8)

2. sudo dpkg-reconfigure console-data 
and select the "qwerty" and "Q Layout with Unicode" 

3. gconf-editor

open desktop>>gnome>>peripherals>>keyboard>>kbd using the tree on the left. Find  "layouts"' and double-click.
Click on "Add" and type in "tr" for turkish (for others, type in the correct acronym).

If this does not work, edit

/etc/X11/xorg.conf

Here is the section that sets up the keyboard.

....

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb,tr"
EndSection
....

Enjoy Ubuntu!

OZ

---

### Post by newbie2 on 2005-10-24
same problem here ...i have a french gateway 2000 anykey azerty keyboard ... cannot change to proper layout via system/preferences/keyboard :confused:
worked well in hoary...upgraded to breezy...

---

### Post by newbie2 on 2005-10-25
[QUOTE=newbie2]same problem here ...i have a french gateway 2000 anykey azerty keyboard ... cannot change to proper layout via system/preferences/keyboard :confused:
worked well in hoary...upgraded to breezy...[/QUOTE]
it's fixed now :)  i have added universe and non free updates on breezy update manager

---

### Post by paulle on 2005-10-27
what non-free updates? can you present here your sources.lst?
tanks a lot

---

### Post by newbie2 on 2005-10-28
[QUOTE=paulle]what non-free updates? can you present here your sources.lst?
tanks a lot[/QUOTE]
via update manager/preferences /add  :

breezy
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
main restricted universe multiverse

---

### Post by Belfagor on 2006-01-16
hi! i dont know whater it is late or not but this solution does work.. you have to remove the Option "XkbVariant" "q" line from xorg.conf files' 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
	Option		"XkbVariant"	"q"

section.

Sedat Mavuzer

---

### Post by baytuni on 2006-01-27
can you explain step by step i'm a newbie:) thanks!!

---

### Post by lorap on 2006-01-27
try to add layout to your keyboard then add the language icon to the panel.
press alt+alt to change the language.
this should work.

---

