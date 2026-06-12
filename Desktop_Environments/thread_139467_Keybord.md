---
title: "Keybord"
date: 2006-03-04
forum: Desktop Environments
---

### Post by Icebear on 2006-03-04
Hi All

Thank you all out there, for your help.With your help I have managed to adjust the xkb Russia phonetic keyboard to what the wife is more happy at. But she is learning a Norther Russian indigenous peoples group language called Nenets and they need some extra specialize letters that needs to be added the Russian alphabet. one letter  as a Unicode number of U+4C8 and U+4C7 (lower and uppercase) is there a way adding this to the keybaord preferable say using maybe the alt key as the Russian keyboard is already full.

---

### Post by Icebear on 2006-03-05
I have started to make progress on the solution. I found  in the xkb file you add the Unicode symbol without the plus(+) sign then xkb gave me the right letter:D . But I still don't know how to make it to be a second group of letters (i.e. capital and lower case) to a keyboard key using something like the Alt key.

---

### Post by Icebear on 2006-03-10
Success here is how I did it thank you for your help out there. The  ubuntu community is great I am pleased to be part of it. .

How to map a keyboard in ubuntu 5.10 (Breezy Badger)

go toX11/symbols diretory, 	by typing cd /etc/X11/xkb/symbols
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

You can use unicode numbers also instead of names. (Don't use the "+"  sighn  ie. use U4C7 not U+4C7)

from
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN	]	};
to
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN,	U04C8,		U4C7	]	};

then save

Then go System>preferences>Keyboard

then click layout options 
then choose third level choosers
and choose button you wish to use for the 2 
To get the 2 letter while tuping hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

---

