---
title: "Mapping different characters to keyboard"
date: 2009-03-26
forum: General Help
---

### Post by Hibbo on 2009-03-26
Hello, or rather Hei!

I am running Ubuntu on my Dell laptop, it has a standard UK keyboard.  I often work in Scandinavia and would like to map the extra vowels ø å æ to rarely used keys on my keyboard (like the square brackets and the stupid reverse apostrophe below esc).

Is this at all possible?  I know I could just set it to a Norsk layout, but that would just be too confusing!

Cheers!

---

### Post by Icebear on 2009-03-26
How to map a keyboard in ubuntu 

go to X11/symbols directory, 	by typing cd /usr/share/X11/xkb/symbols
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

You can use unicode numbers also instead of names. (Don't use the +  sign  ie. U4C7)

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

