---
title: "Custom keyboard layout"
date: 2009-03-01
forum: General Help
---

### Post by darkweasel on 2009-03-01
Hi everyone,

I want to create a custom keyboard layout with the special Esperanto characters &#265;&#285;&#293;&#309;&#349;&#365;, but based on the German layout instead of the US one. (That is: Map Q to &#348;, W to &#284;, Y to &#364;, X to &#264;, Ö to &#308;, Ä to &#292; and Ü to @ - with AltGr the original characters should be able to be accessed)

I found a few instructions, but they say something about editing something in /etc/X11/xkb/symbols - a directory that doesn't exist on my machine.

darkweasel@darkweasel-desktop:/etc/X11/xkb$ ls
base.xml

So, how can I achieve this?

Thanks in advance,
darkweasel

(See also [http://de.lernu.net/komunikado/forumo/temo.php?t=3990&p=2](http://de.lernu.net/komunikado/forumo/temo.php?t=3990&p=2))

---

### Post by Abras on 2009-03-02
Saluton,

Well, I just started learning Esperanto about two weeks ago. And since I use Ubuntu too, it was only a few days after that when I started looking into keyboard layouts. So I did a little digging and this is what I found.

First, I tried the built-in layout, which I found rather clunky and confusing. So then I found [this thread]("http://ubuntuforums.org/showthread.php?t=852353&highlight=esperanto"), and in particular [this post]("http://ubuntuforums.org/showpost.php?p=313950&postcount=8") (linked about halfway down on the first page). I imagine you could use pretty much the same procedure -- just change the keys to map to. I'm not at all sure about what number corresponds to what key, but I'm sure you can find that elsewhere on this forum.

Oh, and there's also this: [http://bertilow.com/komputo/linukso.html](http://bertilow.com/komputo/linukso.html) 
I don't really speak Esperanto yet so it wasn't much help to me, but maybe you do? I couldn't really tell from your post.

Anyways, hope that helps at least a little. If not, don't hesitate to ask away. And I hope to one day talk to you in Esperanto! 

&#284;is,
Abras

EDIT: You may also want to try [this thread]("http://ubuntuforums.org/showthread.php?p=5751130") for another keyboard layout.

---

### Post by Icebear on 2009-03-02
How to map a keyboard in ubuntu 


go to X11/xkb/symbols diretory, by typing cd /usr/share/X11/xkb/symbols
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
then click the other options button
then choose third level choosers
and choose button you wish to use for the 2 
To get the 2 letter while typing hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

---

### Post by darkweasel on 2009-03-03
Saluton &#265;iuj,

Icebear: As I said - there is no /etc/X11/xkb/symbols on my computer somehow.

Abras:
eo: Dankon por via helpo, sed la ligilo al bertilow.com nur diras pri /etc/X11/xkb/symbols. Kaj SCIM nur permesas min je skribi "hx" por "&#293;" - mi povas jam skribi la supersignojn per aliaj metodoj (kiujn mi diris sur la lernu! forumo, vidu anta&#365;e) - la kialo, ke mi volas tion, estas, ke estas kelkfoje tre malrapide tajpi du a&#365; tri klavojn (<circumflex key>h a&#365; <compose>uu).
en: Thanks for your help, but the link to bertilow.com only talks about /etc/X11/xkb/symbols. And SCIM only permits me to write "hx" for "&#293;" - I can already write the accents using other methods (which I mentioned on the lernu! forums, see above) - the reason I want this is that it's sometimes very slow to type two or three keys (<circumflex key>h or <compose>uu).

eo: Mi pensas, ke mia vera problemo estas, ke /etc/X11/xkb/symbols kial ajn ne ekzistas sur mia komputilo.
en: I think my real problem is that /etc/X11/xkb/symbols for some reason doesn't exist on my computer.

---

### Post by Icebear on 2009-03-04
hi 

are you using ubuntu or kubuntu or xubuntu
if ubuntu 
can you try for me in the command prompt 

sudo gedit /usr/share/X11/xkb/symbols/ru

this would be the russian keyboard to see if you have that folder

you can also look it up with your file manager when in your home folder on the left there is a list of places one of them is called File System then from there navigate to symbols

to edit a keyboard map you need to have root permission which is easiest with the command prompt and sudo

---

### Post by Icebear on 2009-03-04
if that does not work use the the search file application. 

you find it at the second to bottom of the list when you hit Places

to find the symbols folder

make sure that when you are searching that you change from your home folder to File Sytem

---

### Post by jtschrock on 2009-03-13
I too am trying to make a custom keyboard.  I've done the steps discribed above.  I've also done the step astutely outlined by O'Donnell

[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

I've done all these steps but my system isn't recognizing my new layout that I've placed /usr/share/X11/xkb/symbols/cw (cw being my layout.  I am wondering why 8.10 doesn't have this stuff in /etc.  Would this somehow affect the recognition of a new layout in my system.

Thanks

---

### Post by jtschrock on 2009-03-14
I obviously don't know what I'm doing here.  Thrashing about as always.

So I'm to create a custom layout for language cw to use on my Ubuntu 8.10 system

I've created a custom layout at:

/usr/share/X11/xkb/symbols/cw



[INDENT]// $XKeyboardConfig$

//
// Keyboard layout to mimic CTGR Chinuk Wawa font (CHINW_4.1.ttf)
// glottalization deadkeyed to <TLDE)
// acute accent deakkeyed to ****+<TLDE>
// phonetic symbols not used in standard orthography eliminated

default
partial alphanumeric_keys modifier_keys 
xkb_symbols "basic" {

    key <TLDE> {	[     grave,	asciitilde	]	};
    key <AE01> {	[	  1,	exclam 		]	};
    key <AE02> {	[	  2,	at		]	};
    key <AE03> {	[	  3,	numbersign	]	};
    key <AE04> {	[	  4,	dollar		]	};
    key <AE05> {	[	  5,	percent		]	};
    key <AE06> {	[	  6,	asciicircum	]	};
    key <AE07> {	[	  7,	ampersand	]	};
    key <AE08> {	[	  8,	asterisk	]	};
    key <AE09> {	[	  9,	parenleft	]	};
    key <AE10> {	[	  0,	parenright	]	};
    key <AE11> {	[     minus,	underscore	]	};
    key <AE12> {	[     equal,	plus		]	};

    key <AD01> {	[	  q,	Q 		]	};
    key <AD02> {	[	  w,	U02B7,		W		]	};
    key <AD03> {	[	  e,	E		]	};
    key <AD04> {	[	  r,	U025B,		R		]	};
    key <AD05> {	[	  t,	T		]	};
    key <AD06> {	[	  y,	U028A,		Y		]	};
    key <AD07> {	[	  u,	U		]	};
    key <AD08> {	[	  i,	I		]	};
    key <AD09> {	[	  o,	O		]	};
    key <AD10> {	[	  p,	P		]	};
    key <AD11> {	[ bracketleft,	braceleft	]	};
    key <AD12> {	[ bracketright,	braceright	]	};

    key <AC01> {	[	  a,	A 		]	};
    key <AC02> {	[	  s,	S		]	};
    key <AC03> {	[	  d,	D		]	};
    key <AC04> {	[	  f,	F		]	};
    key <AC05> {	[	  g,	G		]	};
    key <AC06> {	[	  h,	U02B0,		H		]	};
    key <AC07> {	[	  j,	J		]	};
    key <AC08> {	[	  k,	K		]	};
    key <AC09> {	[	  l,	L		]	};
    key <AC10> {	[ 	U02BC,	U0301,		semicolon,	colon		]	};
    key <AC11> {	[ apostrophe,	quotedbl	]	};

    key <AB01> {	[	  z,	Z 		]	};
    key <AB02> {	[	  x,	U0323,		X		]	};
    key <AB03> {	[	  c,	C		]	};
    key <AB04> {	[	  v,	V		]	};
    key <AB05> {	[	  b,	B		]	};
    key <AB06> {	[	  n,	N		]	};
    key <AB07> {	[	  m,	M		]	};
    key <AB08> {	[     comma,	less		]	};
    key <AB09> {	[    period,	U00E6,		greater		]	};
    key <AB10> {	[     U0294,	slash,		question	]	};

    key <BKSL> {	[ backslash,         bar	]	};
    key <CAPS> {	[ Caps_Lock	]	};
    // End alphanumeric section
};
[/INDENT]

I've also added the following to my file at

/usr/share/X11/xkb/rules/xorg.xml


[INDENT]...
    <layout>
      <configItem>
        <name> cw </name>
        <shortDescription> CW </shortDescription>
        <description> Chinuk Wawa </description>
      </configItem>
    </layout>  
...[/INDENT]

I assumed that once I have done these steps and rebooted, I would be able to see another keyboard option in the System/Preferences/Keyboard drop menu.  

I think there are some steps that I am missing.  I'm reading through a bunch of the xkb documentation to figure this out.  If any of you have quick insight as to what I'm missing, thank you for any responses.


  </layoutList>

---

### Post by darkweasel on 2009-03-29
> **Icebear said:**
> hi 

are you using ubuntu or kubuntu or xubuntu
if ubuntu 
can you try for me in the command prompt 

sudo gedit /usr/share/X11/xkb/symbols/ru

this would be the russian keyboard to see if you have that folder

you can also look it up with your file manager when in your home folder on the left there is a list of places one of them is called File System then from there navigate to symbols

to edit a keyboard map you need to have root permission which is easiest with the command prompt and sudo

First, sorry for not replying... I thought I had this thread on the notification list...

Second, thank you! All manuals I saw talked about this in /etc, but it's in /usr/share! I'm going to try if I manage the rest. ;)

---

### Post by darkweasel on 2009-03-30
OK, I've now managed that Ubuntu recognizes my keyboard layout, but when I add it, I get:
[i]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10502000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/i]

These two commands give:
[i]darkweasel@darkweasel-desktop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "de", "", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "de", "", "lv3:ralt_switch,compose:menu,grp:shifts_toggle,ctrl:nocaps"
darkweasel@darkweasel-desktop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [de,eo]
 model = 
 options = [lv3	lv3:ralt_switch,Compose key	compose:menu,grp	grp:shifts_toggle,ctrl	ctrl:nocaps][/i]

My keymap is attached. (The comments and almost everything else were copied from the German layout, so don't wonder.. I also deleted all the other variants of the German keyboard, was that a mistake?)

---

### Post by darkweasel on 2009-04-06
any1?

---

