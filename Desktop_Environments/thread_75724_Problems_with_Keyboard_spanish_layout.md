---
title: "Problems with Keyboard spanish layout"
date: 2005-10-14
forum: Desktop Environments
---

### Post by danielet on 2005-10-14
Hi comunity ubuntu members.

    Strange thing happens with my fresh brezzy install. My keyboard layout doesn't work correctly, some signs are mixed up. The keyboard is set to "es" Spain, in my xorg config as well as in gnome setup, so I don't understand why it doesn't work. It's very strange because in hoary worked correctly and in the preview version also worked well. Keyboard is also set up to generic 105 keys. Can somebody help me ?

sorry for my english.

---

### Post by freak42 on 2005-10-14
I have the same/similar problam with swiss-german (ch-de) keyboard layout. it it selected in the keyboard settings tool but actually the en-us keyboard layout is used. switching to another keyboard layout in above tool doesn't do anything. this is after upgrading to breezy

---

### Post by gerrit74 on 2005-10-14
[QUOTE=danielet]Hi comunity ubuntu members.

    Strange thing happens with my fresh brezzy install. My keyboard layout doesn't work correctly, some signs are mixed up. The keyboard is set to "es" Spain, in my xorg config as well as in gnome setup, so I don't understand why it doesn't work. It's very strange because in hoary worked correctly and in the preview version also worked well. Keyboard is also set up to generic 105 keys. Can somebody help me ?

sorry for my english.[/QUOTE]

Hello,

I'm repairing computers and have a very small working space.(and spare parts
for example key-boards.) Sometimes i put my linux computer aside and build it up
later on,grab a key-board(a different one) and have the same problem as you have.
With system-preferences-keyboard I managed to get the keys working all-right,but you have to try which can take a while.

---

### Post by mio on 2005-10-14
Hi, same problem for me when I change keyboard layouts to Norway! 

Anyone have a solution?

---

### Post by danielet on 2005-10-14
Solved the problem.
     I did it like this...System, preferences,keyboard, then cliked on distributions, select add , looked the keyboard layouts in the pictures, and select yours. I selected English international for my Toshiba satellite. All working ok now

Hope helps to someone.

---

### Post by freak42 on 2005-10-14
adding swiss /german keyboard layout in system prefs doesnt help me. it lists the keyboard layout ok but you cannot really select it.
i installed language-pack-de
language-pack-de-base
language-pack-gnome-de
language-support-de 
etc... however this didnt help any

thanks for any help in advance

---

### Post by Bulletproof_Cupid on 2005-10-14
I also have problems with setting up keyboard layout (latvian layout in my case).

In System > Preferences > Keyboard > Layouts, I Add Latvia Apostrophe (') variant and set it as default. Even after restarting I don't get the latvian symbols after the apostrophe key.

It was nice to finally see a distro having the two most common latvian layouts built-in (with apostrophe or tilde dead-keys), but sadly it doesn't just work (tm) yet..

---

### Post by valter on 2005-10-14
same here with Estonian

(temporary solution:
sudo gedit /etc/X11/xorg.conf

and set 
Option		"XkbLayout"	"!!!!YOR LANGUAGE HERE (example: et or es)!!!!"

Then restart X (Alt+Crtl+<--)

When gnome starts again it asks a question. Answer use X settings and DON'T mark remember answer.

Problem is that for me third level buttons doesn't work

)

Does someone know how to do similar in gnome settings?

---

### Post by Bulletproof_Cupid on 2005-10-14
My Option "XkbLayout" was already set to "lv" by GNOME config, but I still can't write latvian symbols. I tried adding Option "XkbSymbols" "apostrophe", but it didn't help either. I'm not a linux guru so I don't know what else can I try to do.

Previously I used an external lv file, had to edit the xorg.conf and had to add some kind of setxkbmap to startup programs. But now I wan't to use the official Ubuntu setting files, etc., because they're there.

---

### Post by paulle on 2005-10-14
keyboard-switcher in gnome
The keyboard switcher in gnome doesn't work for me.
Always remains with us-layout and i can't switch to de or es-layout.

any idea? thanks for help.

---

### Post by mio on 2005-10-14
When I did the temporary solution from valter I got it right;

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"no"

Thanks :)

---

### Post by neutro on 2005-10-14
Yet another mee too post. The keyboard layout switcher applet doesn't work for me, too, and that since about 2 weeks (I was using the Breezy Preview and 2 weeks ago it worked fine).

For those of you for which the switcher is broken, you can try 
```
setxkbmap --model <your keyboard model> layout <your layout> -variant <your variant>
```
and see if it works for you. If you find that your keymap is borked, you can also try
```
xmodmap /usr/share/xmodmap/xmodmap.<your layout>
```
and wish that the keyboard switcher / layouts are fixed.

---

### Post by Bulletproof_Cupid on 2005-10-14
I finally managed to fix my problem. I added 

Option  "XkbVariant"  "apostrophe"

right after the line with my

Option  "XkbLayout"  "lv"

Now I can write in latvian just like I do in MS Windows.


Everyone else, needing level3-keys for language specific symbols, should check out /etc/X11/xkb/symbols/ directory. There are files like en, lv, es - keymaps for each language. Open yours with vi or gedit. There should be a basic keymap, and further down the level3-key variants. Choose the one you prefer and then modify your /etc/X11/xorg.conf . Check whether XkbLayout is your language code, and add XkbVariant name you chose for level3-key map. Restart. A dialog box should appear warning you about different settings in GNOME and Xorg. Choose to keep the Xorg settings and there should be no more problems.

---

### Post by alper_tr on 2005-10-15
I have the same problem with the turkish keyboard layout. I ve chosen turkish keyboard, however even it showed turkish on language icon it remained english and it didnt function.. seems like its bug

---

### Post by kranz on 2005-10-26
[QUOTE=valter]same here with Estonian

(temporary solution:
sudo gedit /etc/X11/xorg.conf

and set 
Option		"XkbLayout"	"!!!!YOR LANGUAGE HERE (example: et or es)!!!!"

[/QUOTE]
Replaceing "us" to "et" doesn't help to get estonian layout... I found out that it's "ee" You have to put in for estonian layout...

---

### Post by paulle on 2005-10-26
i tried everything, butb the problem still remains.  paulle

---

### Post by guandul on 2005-10-31
[QUOTE=Bulletproof_Cupid]

Option  "XkbVariant"  "apostrophe"

right after the line with my

Option  "XkbLayout"  "lv"

[/QUOTE]

It worked for me, I have an US keyboard and I needed the dead keys so I can write the accents in spanish and french. 
1. Go to /etc/X11/xkb/symbols and open the file matching your keyboard, in my case us. 
2. Look for the type of layout variant you want to use, in my case "U.S. English - International (with dead keys)".
Just above this line copy the xkb_symbols tag, in my case "intl".
3. Edit the file /etc/X11/xorg.conf, search for the Option "XkbLayout" "<Your_layout >", in my case:
        Option          "XkbLayout"     "us"
And add a line with your layout variant:
        Option          "XkbVariant"    "intl"

Save the file and restart your computer.
As Bulletproof_Cupid says:
A dialog box should appear warning you about different settings in GNOME and X. Choose to keep the X settings and there should be no more problems.

---

### Post by sawthpaw on 2005-11-02
Ladies/Gents, 

I was surprised to find out, that following the 5.04 upgrade, the keyboard layout was not behaving as before (and expected).
Here is another solution (more of them is better than none - although I admit it lacks a certain elegance - heck, it worked !).
So this is what I did : (from the user account)
- I edited .bashrc to force {in my case} the following settings : 
export LANG=fr_CA
export LANGUAGE=fr_CA
- I made sure the keyboard layout was at US-English /with dead keys.
- Also checked that the language from the [Preferences] sub-menu was on french.
-> Finally what made it "click" for me, was when I used : 
System -> Preferences -> Sessions | Startup Programs Tab -> Add/Edit/Delete, to which I added : setxkbmap 
{with no parameters ... go figure}.  Regardless, it worked, I tested with a logout and a reset of X (ctrl-alt-backspace).

Voilà, hope it helps someone, anyone.
Tooldes,

SP.

---

### Post by neymac on 2005-11-02
[QUOTE=sawthpaw]Ladies/Gents, 


[COLOR="Blue"]System -> Preferences -> Sessions | Startup Programs Tab -> Add/Edit/Delete, to which I added : setxkbmap [/COLOR]

Voilà, hope it helps someone, anyone.
Tooldes,

SP.[/QUOTE]
I made just the blue things and worked fine for Brazilian Portuguese, with US-International Keyboard (with dead keys).

Thank you very much for the usefull help

---

### Post by shane2peru on 2005-12-09
I had the same problem and found the logical answer without having to gedit config files.  You can change keyboard layout all day long, but that isn't going to help you.  The answer is here:  [http://www.ubuntuforums.org/showthread.php?t=99063&highlight=%93Keyboard+Layout+Switcher%94](http://www.ubuntuforums.org/showthread.php?t=99063&highlight=%93Keyboard+Layout+Switcher%94)

Basically it is:

Click on blank space on your panel **Add to Panel** -- Then scroll down to **Keyboard Indicator**and add it.  If you haven't played around to much with the settings of your keyboad this will put an indicator on your panel.  (I had to undo everything that I had done to get it to work the way it should, however if you don go checking a bunch of boxes trying to get it to work it works easily)  When you click the button it switches it for you so you can type your &#225;&#237;&#233;&#250;&#239;&#252;&#235;&#191;&#161;&#241; charaters all day long.  Enjoy!:p 

Shane

---

### Post by runlevel0 on 2005-12-09
Try setting the correct keyboard from the Preferences > Keyboard menu, sometimes the desktop environment is set to US English by default.

There is also an desktop applet to change keyboard layouts that is set to US by default and could change your settings if you add it to the panel.

---

### Post by ashrack on 2005-12-11
[QUOTE=valter]same here with Estonian

(temporary solution:
sudo gedit /etc/X11/xorg.conf

and set 
Option		"XkbLayout"	"!!!!YOR LANGUAGE HERE (example: et or es)!!!!"

Then restart X (Alt+Crtl+<--)

When gnome starts again it asks a question. Answer use X settings and DON'T mark remember answer.

Problem is that for me third level buttons doesn't work

)

Does someone know how to do similar in gnome settings?[/QUOTE]
Also had to manually input to get SLOVENINAN keyboard. Although I've set in GNOME for SLOVENIAN and choose the default it never worked.
ps. We should file a BUG REPORT since this apperantly is a bug. Anyone filled one yet?

---

### Post by shane2peru on 2005-12-11
[QUOTE=ashrack]Also had to manually input to get SLOVENINAN keyboard. Although I've set in GNOME for SLOVENIAN and choose the default it never worked.
ps. We should file a BUG REPORT since this apperantly is a bug. Anyone filled one yet?[/QUOTE]

Ashrack,

If you just see post #20 in this forum, I think this will solve your issue a little easier.  It takes out the manual part, and you shouldn't need to file a Bug Report.  Unless I'm  missing your problem.

Shane

---

### Post by ashrack on 2005-12-13
[QUOTE=shane2peru]Ashrack,

If you just see post #20 in this forum, I think this will solve your issue a little easier.  It takes out the manual part, and you shouldn't need to file a Bug Report.  Unless I'm  missing your problem.

Shane[/QUOTE]
How do I find post #20 in this forum?

---

### Post by shane2peru on 2005-12-13
What I'm refering to is actually the Post Count in this thread.  #20 is the last post on Page 2.  Hope that clarifies.  

Shane

---

### Post by ashrack on 2005-12-13
Sweet works like charm
Well I believe it still is a bug, because if U don't do what in the other thread is told U can click all day long and still wouldn't be able to switch. 
UBUNTU programers could place a warning or something so we would know what else to do

---

### Post by UphillSkier on 2005-12-24
I just found the solution in another thread 

[http://ubuntuforums.org/showpost.php?p=465307&postcount=13](http://ubuntuforums.org/showpost.php?p=465307&postcount=13)

and am telling everyone I know about it.   Works like a dream.

---

### Post by Sedat on 2006-02-20
[QUOTE=alper_tr]I have the same problem with the turkish keyboard layout. I ve chosen turkish keyboard, however even it showed turkish on language icon it remained english and it didnt function.. seems like its bug[/QUOTE]

&#304; think i solved problem by this way;
in the file etc/x11/xorg.conf

in the
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
.............

i added the line;
	Option 		"XkbVariant" 	"basic"

under the line;
	Option		"XkbLayout"	"tr"


Kolay Gelsin.

---

### Post by izi on 2007-03-20
See 
[http://ubuntuforums.org/showthread.php?p=2326135#post2326135](http://ubuntuforums.org/showthread.php?p=2326135#post2326135)

---

### Post by plays_with_fire on 2007-03-20
> **valter said:**
> 
(temporary solution:
sudo gedit /etc/X11/xorg.conf

and set 
Option		"XkbLayout"	"!!!!YOR LANGUAGE HERE (example: et or es)!!!!"

Then restart X (Alt+Crtl+<--)

When gnome starts again it asks a question. Answer use X settings and DON'T mark remember answer.



My layout was working just fine (US-INTL) before I messed with the X settings, but I was getting an annoying error message when gnome started. So I changed the X settings and when gnome asked the question I went with using the gnome layout settings and marked remember answer. Now I still get the error and my keyboard layout doesn't work, damn.

---

### Post by Static-X on 2007-04-30
System/preferences/keyboard select "US_English INTL_Dead Keys"
(Generic 101-key PC)

I did logout and later... use:

Left SHIFT  (hold) + ~ + n = Ñ  
Left SHIFT  (NO hold)+ ~ + n = ñ

' + a = á    

 :)

---

