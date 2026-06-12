---
title: "Keys do not work in GNOME"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Reb on 2005-10-28
NOTE: my b, f and p keys do not work (the keyoard shortcuts dialog sees them as
X86AudioNext, X86Audiorev and X86Audiolay, resectively). Instead o coying and
asting every time I need one o these I will simly ski the letter and leave you
to ill in what's missing unless the world is undeciherale otherwise.
This is the strangest ug I have ever seen. I am using the Dvorak layout, and
switching to any other layout and ack solves the rolem until I log ack out and
in. This is a huge issue or me ecause my ssword contains a b and I can't coy and
aste a b rom anywhere beore login. Until today, it was only the last o the three
keys that didn't work.

ertinent inormation:
uname -a
Linux brother 2.6.12-9-amd64-k8 #1 Mon Sep 26 23:16:46 BST 2005 x86_64 GNU/Linux
ully udated reezy

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "dvorak"
EndSection

Keyoard model rom System > reerences > Keyoard dialog is Generic 105-key (Intl)
PC. U.S. English Dvorak is the currently selected layout and is the to choice in
the list. elow it is U.S. English layout (not checked).

The keyoard works ine in KDE/Kuuntu.

---

### Post by Reb on 2005-10-28
And something else strange has happened: I've switched the keyboard layout from US English to US English Dvorak. Whenever I type in a program, the keypresses
are Dvorak, but Metacity still launches shortcuts with US English (ie, Firefox
(Control-Alt-I) is launched by the US English I instead of the Dvorak I (which
is located where the G key normally is). I think this is related.

This is a desktop, with a Microsoft Natural Keyboard (that's the one that's split in the middle).

This was copied from my b at [http://bugzilla.ubuntu.com/show_bug.cgi?id=16479](http://bugzilla.ubuntu.com/show_bug.cgi?id=16479). Maybe someone ese has had this probm...

---

