---
title: "Transliteration of sanskrit or other indic languages with xkb"
date: 2008-01-12
forum: Desktop Environments
---

### Post by Arjunanda on 2008-01-12
I have created a Translit keymap for XKB for transliteration of sanskrit, hindi or other indic languages with diacritics. I have submitted this keymap for inclusion of the main distribution of XKB, but until my contribution is validated and included in the distribution, I am giving it here.

You will find the keymap attached to this posting. Below you will find instructions.

From the README -file:
Translit is a keymap for transliterating indic scripts into latin, utilizing the standard transliteration schemes: IAST, NLCR and ISO 15919. Earlier there was no ready made keymap available, making it very difficult to utilize the standard transliteration schemes.

Now it can be used through keyboard layout switchers by adding the option
India - IAST/NLCR transliteration / translit

Note: Normal western-european QWERTY keyboard comes by default.
To get long wovels (&#257;&#256;, &#299;&#298;, &#363;&#362;), use:
Right Alt + a => &#257;,
Right Alt + A => &#256; etc.

To get retroflex consonants (&#7693;D,&#7789;&#7788;, &#7751;&#7750;), use:
Right Alt + d => &#7693;
Right Alt + D => &#7692;

To get &#7751;&#7750;, use Right Alt + n/N,
To get &#7749;&#7748;, use Right Alt + g/G
To get ñÑ, use Right Alt + j/J

To get &#2384;, use Right Alt + X, to get &#784;  use Right Alt + Shift + X

Installing it

Unzip it
# unzip translit-in.zip

and copy the files to following locations:
/usr/share/X11/xkb/symbols/in
/usr/share/X11/xkb/rules/base.lst
/usr/share/X11/xkb/rules/base.xml

or alternatively (depending of your distribution) to:

/etc/X11/xkb/symbols/in
/etc/X11/xkb/rules/base.lst
/etc/X11/xkb/rules/base.xml

---

### Post by K.Mandla on 2008-01-13
Moved to Desktop Environments.

---

