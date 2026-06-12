---
title: "Mapping [caps] to [esc]"
date: 2005-10-11
forum: Desktop Environments
---

### Post by Dustismo on 2005-10-11
Hello,

As an emacs user and NOT A COMPLETE JERK (heh :smile: ) I would like to eleminate the capslock key and replace it with esc. 

I have done the whole .Xmodmap (see: [http://iew3.technion.ac.il/CC/Comp_news/muo-may02/xwin/xkeys.html](http://iew3.technion.ac.il/CC/Comp_news/muo-may02/xwin/xkeys.html))

but Gnome doesn't seem satisfied with this..  It randomly reverts back.. or has trouble with disabling the led in the keyboard..  Aargh..

I would like to change the keymap at the kernel level (i.e. caps-lock will be turned into esc for everything, system wide, forever..)  Is this possible?  I'm sure I have to edit some keymap file, but I'm not sure wich one. 

Thanks,
Dustin

---

### Post by Alexander Kirillov on 2005-10-11
[QUOTE=Dustismo]Hello,

As an emacs user and NOT A COMPLETE JERK (heh :smile: ) I would like to eleminate the capslock key and replace it with esc. 

I have done the whole .Xmodmap (see: [http://iew3.technion.ac.il/CC/Comp_news/muo-may02/xwin/xkeys.html](http://iew3.technion.ac.il/CC/Comp_news/muo-may02/xwin/xkeys.html))

but Gnome doesn't seem satisfied with this..  It randomly reverts back.. or has trouble with disabling the led in the keyboard..  Aargh..

I would like to change the keymap at the kernel level (i.e. caps-lock will be turned into esc for everything, system wide, forever..)  Is this possible?  I'm sure I have to edit some keymap file, but I'm not sure wich one. 

Thanks,
Dustin[/QUOTE]
I do not know how it can be done at kernel level, but you should be aware that X11 has two mechanisms for keyboard mappings: old one (xmodmap) and newer xkb. Almost all recent tools (e.g., gnome keyboard switcher) use xkb. Maybe you should try this? There are plenty of manuals available on google; basically, you'll need to edit file like 
/usr/lib/X11/xkb/symbols/us

---

### Post by HermanAB on 2005-10-11
Google for this: "linux switch Caps Lock and Ctrl keys"

You'll find lots of good info:

Sorting It All Out : Some people hate the CAPS LOCK key
Swapping the caps and left ctrl keys is one of the first things I do when ...
The Japanese IME actually uses Alt/Shift/Ctrl+Caps Lock to switch among script ...
blogs.msdn.com/michkap/archive/2005/09/21/471982.aspx - 64k - Cached - Similar pages

Halfbakery: mOVE cAPS lOCK
Switch Caps -> Ctrl for Win 9x/ME [http://sysinternals...es/ctrl2cap95.shtml](http://sysinternals...es/ctrl2cap95.shtml) ...
Lots of people feel that the caps lock key is useless anyway, and certainly ...
[www.halfbakery.com/idea/mOVE_20cAPS_20lOCK](www.halfbakery.com/idea/mOVE_20cAPS_20lOCK) - 41k - Cached - Similar pages

The Linux keyboard and console HOWTO: Examples of use of loadkeys ...
Switching Caps Lock and Control on the keyboard (assuming you use keymaps 0-15;
... "Can the Shift, Ctrl and Alt keys be made to behave as toggles?" ...
[www.tldp.org/HOWTO/Keyboard-and-Console-HOWTO-15.html](www.tldp.org/HOWTO/Keyboard-and-Console-HOWTO-15.html) - 8k - Cached - Similar pages

Keys and Terminal Configuration
Keys and Linux Terminal Configuration. To really understand and work with key
mapping, ... CTRL S - Stop scrolling, may use "scroll lock" for this function. ...
[www.comptechdoc.org/os/linux/usersguide/linux_ugterminal.html](www.comptechdoc.org/os/linux/usersguide/linux_ugterminal.html) - 17k - Cached - Similar pages

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

