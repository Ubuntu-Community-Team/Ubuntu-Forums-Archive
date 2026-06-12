---
title: "Mini 9 Super Key?"
date: 2008-12-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by klange on 2008-12-18
Alright, I've been searching around and I can't seem to find an answer to this:
I want my Windows key to be a super key, as it should, and before I go punching in a custom keymap for it, I'd like to know where the Dell modifications are that make it fullscreen things. I know the key is sending the write keycode to be read as the Windows key because changing options around in "Layout Options" in gnome-keyboard-properties gets it doing what I want, but only until I reboot, at which point, I'm back to a fullscreen key. With the firmware update that I have yet to look at, I have no use for a dedicated full screen key and would much rather mirror my standard setup using it as a super key. Also, I have an external keyboard that I want to use with it (which, of course, has an F11 key), and I get the same effect on it (which, of course, is not what I want).

So, does anyone have a definitive answer on where the Dell keymap modifications are?

---

### Post by ytsejam1138 on 2008-12-18
I installed a program called XKeyCaps (it's available in the Ubuntu universe repos). This will give you a GUI of the keyboard which will allow for easier remapping of the keys. Then you click on write output and make sure you add:

    xmodmap ~/.xmodmap-`uname-n`

to your sessions and your good to go.  I have a Dell Mini with 8.10 installed and the Windows key is the SuperKey.  The Fullscreen (F11) is Fn+Z. I didn't remap these keys, this was after a stock install.  I don't think you can remap a Fn+ another key.

---

### Post by klange on 2008-12-18
> **ytsejam1138 said:**
> I installed a program called XKeyCaps (it's available in the Ubuntu universe repos). This will give you a GUI of the keyboard which will allow for easier remapping of the keys. Then you click on write output and make sure you add:

    xmodmap ~/.xmodmap-`uname-n`

to your sessions and your good to go.  I have a Dell Mini with 8.10 installed and the Windows key is the SuperKey.  The Fullscreen (F11) is Fn+Z. I didn't remap these keys, this was after a stock install.  I don't think you can remap a Fn+ another key.
This isn't an answer to my question, it's what I was going to do anyway ;)

**e**: Some tips for you, though:
First off, you don't need to add anything to your session, just make sure the file is called ".Xmodmap" (or some other name that xmodmap will find on start up).
Second, if you're doing simple edits, you can just use xmodmap to dump the current map with `xmodmap -pke > .Xmodmap`, and then edit it.

---

### Post by iggykoopa on 2008-12-19
from what I've heard the newer bios updates added FN + Z as f11 and FN + X as F12 if your still using bios A01 you may want to upgrade to get your function keys.

edit: if your using the stock dell install it's probably the program maximus thats doing the fullscreen stuff.

---

### Post by yellowbean on 2009-01-07
Thanks! I had this exact question and maximus is indeed the answer. I just unchecked it in the System->Preferences->Sessions menu and my Super key is behaving normally!

---

