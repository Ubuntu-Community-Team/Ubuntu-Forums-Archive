---
title: "Inserting Diacritic Characters"
date: 2005-07-06
forum: Desktop Environments
---

### Post by zoqaeski on 2005-07-06
Due to the nature of the things I use my system for, I need to be able to type extended latin characters. Does anybody know the keyboard shortcuts for doing these, without having to change keyboard to the US-International one? In windows, I was able to insert almost any character by holding ALT+ the unicode point number of the character I wanted (e.g. ALT+228 gave me a lowercase 'a' with an umlaut).

Does anyone know the shortcuts for Linux?

cheers
Robbie

---

### Post by Sye d'Burns on 2005-07-06
[QUOTE=zoqaeski]I was able to insert almost any character by holding ALT+ the unicode point number of the character I wanted (e.g. ALT+228 gave me a lowercase 'a' with an umlaut).

Does anyone know the shortcuts for Linux?

cheers
Robbie[/QUOTE]

I'm not familiar with Diacritic characters myself but I found this on [Wikipedia](http://en.wikipedia.org/wiki/Diacritic) :


> In GNOME applications (found on many GNU/Linux and UNIX computers) abritrary Unicode characters may be entered by holding down the ctrl and shift keys while typeing the hexadecimal codepoint. After releasing ctrl-shift the digits will be converted into the symbol. For example ctrl-shift 1E3 produces &#483;.

With Unicode it is also possible to combine diacritical marks with most characters. 

It works! ctrl+shift+228=&#552;
---edit----
on second thought, that isn't an a with an umlaut :\

---

### Post by Sye d'Burns on 2005-07-06
>  Windows NT and its descendants Windows 2000 and Windows XP make extensive use of UTF-16 as an internal representation of text. UNIX-like operating systems such as GNU/Linux, Plan 9, BSD and Mac OS X have adopted UTF-8, as the basis of representation of multilingual text. 

A little more research has led me to this [tidbit.](http://en.wikipedia.org/wiki/UTF-8)

---

### Post by waster on 2007-04-16
This doesn't work for me in Feisty. No combination of alt, shift and ctrl with hex unicode entry seems to work produce anything at all.

are you able to enter unicode characters by their hex code?

---

### Post by waster on 2007-04-16
got it. in feisty you must do this:

hold down ctrl-shift

press U
type the hex unicode value
the typed letters should appear underlined
release keys: the unicode symbol should replace the underlined characters
in OpenOffice, you must press ENTER before releasing the keys, otherwise it just keeps the underlined text.

---

### Post by engine on 2007-05-03
Thanks, friend! that's a function I've been looking for for years ...

---

### Post by whitefort on 2008-03-03
> **waster said:**
> got it. in feisty you must do this:

hold down ctrl-shift

press U
type the hex unicode value

Thank you SO much for this.  I've been tearing my hair out trying to get an 'é' (which I use a lot!)

---

