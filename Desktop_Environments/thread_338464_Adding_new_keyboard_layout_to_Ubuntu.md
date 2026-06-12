---
title: "Adding new keyboard layout to Ubuntu"
date: 2007-01-14
forum: Desktop Environments
---

### Post by daniel1988 on 2007-01-14
I'm not satisfied with none of Ubuntu's built in keyboard layouts for Serbian language ("?" is in the wrong place - it should be at it's original place; "/" is missing - I tried all 4 layouts for Serbia, none corrects this), so I want to add one new. This one from the attachment, works well on Gentoo (Xorg 7.1). It just needs to be extracted in: /urs/share/X11/xkb/symbols/pc/ and "activated" by typing in terminal:
```
setxkbmap srp latin
```

How to get this layout to work in Ubuntu (and to switch between it and English one, like the others - ex. using alt+shift)?

I tried:
```
sudo mkdir -p /usr/share/X11/xkb/symbols/pc
sudo cp /home/daniel1988/srp .
```
but
```
daniel1988@laptop:~$ setxkbmap srp latin
Error loading new keyboard description

```

Cheers,
Daniel

---

### Post by Icebear on 2007-01-14
This was how I changed some of the Russian keyboard letters for my wife. 

How to map a keyboard in ubuntu 5.10 (Breezy Badger)

go to X11/symbols diretory, 	by typing cd /etc/X11/xkb/symbols
then find layout you want to change

for example ru (for Russian)

make a backup of the selected file,	sudo cp ru ru_backup
then load the file up to edit,	sudo gedit ru

find the section you want in it to change 
in my case the phonetic layout

then swap changes you wish to make

for example: from
key	<LatV> {	[    Cyrillic_zhe,    Cyrillic_ZHE	]	};
to
key	<LatV> {	[    Cyrillic_ve,    Cyrillic_VE	]	};

If you want to add a  2nd letter to a key then at the spot where it describes the level

in the Russian phonetic spot change the level from ALPHABETIC to FOUR_LEVEL_ALPHABET or  FOUR_LEVEL

for example from
key.type[group1]="ALPHABETIC";
to
key.type[group1]="FOUR_LEVEL_ALPHABETIC";

and at the key add the letter you want to change after the first two settings.

You can use unicode numbers also instead of names. (Don't use the +  sighn  ie. U4C7)

from
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN	]	};
to
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN,	U04C8,		U4C7	]	};

then save

Then go System>preferences>Keyboard

then click layout options 
then choose third level choosers
and choose button you wish to use for the 2 
To get the 2 letter while typing hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

---

### Post by daniel1988 on 2007-01-16
I'm really not willing to edit it key by key.

Is there a way to make the file from attachment to do what it is meant for?

--Daniel

---

