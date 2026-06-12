---
title: "Language Login problem"
date: 2009-03-01
forum: General Help
---

### Post by jeltzz on 2009-03-01
I've looked through the forums, and read some similar problems, but haven't found a workable solution. I'm running 8.10, and have 4 keyboard layouts set-up, including Greek.

Now when I boot up and go to log in, the input language is appearing as Greek, which isn't the default, and so neither login nor password is accepted.

I opened up a console terminal to try and access the xorg.conf file, but even the input language there appears to be greek (judging by the few characters that aren't displayed as diamonds). So, as it stands I can't login through the GUI or through the terminal, and the keyboard is locked to Greek.

Any thoughts?

---

### Post by GeorgeCm on 2009-03-01
I have i believe the same problem! Again with Greek language. I cannot login because i cannot change the language in the login menu!

---

### Post by jeltzz on 2009-03-02
Sorry to hear you're having the same problem George.

I managed to boot up from an Ubuntu CD, and mount my hard-drive partition, and thus access the xorg.conf file which I thought may hold some clues. But, sadly, it has no "Input Device" section listed, so I'm not sure what to add/change.

So, if someone knows what I should be looking for, and what to change, I think I can do it, I just need to know what.

---

### Post by jeltzz on 2009-03-04
This is how I solved it:


I booted up from a CD, mounted the hard-drive, then ran through some options.
I tried running the console-setup package. But that didn't seem to have any effect - when I rebooted the problems were exactly the same.
I couldn't find enough understandable instructions to check my default locale and change that.
What I did do was add details to the xorg.conf, specifically I added:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

---

