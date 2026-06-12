---
title: "Custom Keyboard mapping with Gnome"
date: 2006-11-26
forum: Desktop Environments
---

### Post by bmhm on 2006-11-26
[SIZE="3"][FONT="Bitstream Vera Sans"]** WARNING ** VERY sophisticated question ** WARNING **

Hi all,

I'm a german Ubuntu user and can access a lot of funny signs by using the "alternate graphics" key [Alt Gr] or [Alt Gr] plus [Shift].

When I press AltGr + s i get a german sz-ligature: ß
But I already got that char on my german keyboard next to the 0 (nil, zero).

So... I'd like to change the key combination AltGr + s to the german long s.
Unicode: U+017F ›Latin small letter long s‹ (Lateinischer Kleinbuchstabe langes s)
HTML: &#x017F; (sedezimal) or &#383; (dezimal).
If you got UTF-Encoding enabled, look at this: &#383;
No, it's not an " f ".

Ok, so how can I change it?

I'd love to get an answer for such a sophisticated question!

Regards,
-> Benjamin[/FONT][/SIZE]

---

### Post by bapoumba on 2006-11-26
Hi,

you might want to have a look at [xmodmap]("http://www.in-ulm.de/~mascheck/X11/xmodmap.html"), but also at the "compose" key (in System > prefs > keyboard where you can define the "compose" key, I have the right ctrl enabled). Just give it a try in a simple editor  (gedit for ex.). I do not have a german layout keyboard, so I cannot check if the exact letter you are trying to get is available that way.

---

### Post by bmhm on 2006-11-26
> **bapoumba said:**
> ... but also at the "compose" key (in System > prefs > keyboard where you can define the "compose" key, I have the right ctrl enabled). Just give it a try in a simple editor  (gedit for ex.). 

[FONT="Verdana"]And how do I bind a char to my new compose key?

Well, I did the following so far:
xmodmap -e "keycode 39 = s S 0x17f section ssharp section"

where 0x17f should be my long s [Wikipedia-Link]("http://en.wikipedia.org/wiki/Long_s")

So... when I do remap a key with xmodmap, will it change it function in gnome as well?
// Edit: no didn't work for gnome :(
xmodmap doesnt save the changes... why?[/FONT]

---

### Post by bmhm on 2006-11-27
> **bapoumba said:**
> Hi,

you might want to have a look at [xmodmap]("http://www.in-ulm.de/~mascheck/X11/xmodmap.html")

[FONT="Verdana"]It says:
> Some hints about xmodmap(1) and the X11 keyboard model
"If you're thinking that this is all senselessly complicated... you're right." - Jamie Zawinski

So i did:
# touch .xmodmaprc
# xmodmap -e "keycode 39 = s S 0x17f section ssharp section"

didn't work either :(

So how to use that ***** compose-key?[/FONT]

---

### Post by bmhm on 2006-11-28
[FONT="Verdana"]*up*

Hey ist das denn soooo schwer eine Taste neu zu setzen?

Can it be THAT hard to remap a single key?

I'm sure there's at least one person out there who knows...[/FONT]

---

### Post by Icebear on 2006-11-28
This is my reminder on how to change the keyboard mapping

How to map a keyboard in ubuntu 5.10 (Breezy Badger)
it also works with 6.10

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

### Post by bmhm on 2006-12-29
> **bmhm said:**
> [FONT="Verdana"]
So i did:
# touch .xmodmaprc
# xmodmap -e "keycode 39 = s S 0x17f section ssharp section"
[/FONT]

[FONT="Arial"]Answer was easy:
# xmodmap -e "keycode 39 = s S U017F section U017F section"[/FONT]

---

### Post by wackimonki on 2007-04-23
Thank you SO much for posting that Icebear.

It worked liked a dream.

I change my - key (to the right of 0) to _ by default. I write a lot of Ruby code and it should come in handy.

---

