---
title: "Restarting X"
date: 2008-01-27
forum: Desktop Environments
---

### Post by Salazar420 on 2008-01-27
So, on my desktop I am able to use the quick restart feature for the X desktop with (ctrl + alt + backspace). On my laptop, this feature doesn't work. ctrl+alt+backspace does absolutely nothing, and ctrl+alt+delete brings up the logout screen... you know, shutdown, restart, hybernate, suspend, and the like. Why is the quick restart for X not working, and how might I go about making it work? Responces are greatly appreciated.

---

### Post by p_quarles on 2008-01-27
Hopefully, someone else can give you a more comprehensive answer, but I can suggest a workaround.

Open a console login by pressing ctrl-alt-F1 (of course, you may run into the same problem with this). If that works, you can run:
```
sudo /etc/init.d/gdm restart
```and the login screen will pop back up in a few seconds.

Not an ideal solution, I know, but a possible stopgap.

---

### Post by Salazar420 on 2008-01-27
Worked like a charm. I wonder, perhaps I can assign this command to the ctrl+alt+backspace hotkeys... or something like this. Is this command the equivalent or the typical ctrl+alt+backspace function? I can't imagine so, seeing as how it appears to require root privileges... idk though, will wait and see what others say. Thanks for your responce.

---

### Post by frigaut on 2008-01-27
that's weird.
Did you check that xev is giving you "backspace" when you press the backspace key?
(just type "xev", put your cursor in the created window and press the backspace key).

---

### Post by Salazar420 on 2008-01-28
> **frigaut said:**
> that's weird.
Did you check that xev is giving you "backspace" when you press the backspace key?
(just type "xev", put your cursor in the created window and press the backspace key).

This is, to the best of my ability, the output of the test you had me run. I can not be sure if this is the exact output, for every motion I make with the cursor, every key I press, is backed by newton's law, and shows reaction; therefore, moving the output up to an intangible, unreachable location... eh, you get what I mean (I have a compulsive habit of making the simplest things complicated and anything but comprehensive. Anyway, there it is. I don't know what I'm supposed to be looking for though.
> 
KeyRelease event, serial 30, synthetic NO, window 0x4000001,
    root 0x58, subw 0x0, time 3274515802, (89,155), root:(738,220),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False


P.S. Thanks for the responce.

---

### Post by Salazar420 on 2008-01-28
I ran a 'xev > new.txt' command, then 'cat new.txt' and found that the above information is the accurate output you were searching for. I still, however, do not know what to make of the information, other than the fact that it did, indeed, register my (backspace) keystroke. What do you think?

lol...P.S. You just gatta love how the output input into the forum make the smiles and frowns....

---

### Post by frigaut on 2008-01-28
as far as I can tell, it looks good.

Would you have re-defined a shortcut somewhere that would have superseeded the regular ctrl-alt-backspace?
other than that, I have no more clue.
and by the way, what's your laptop?

---

### Post by Salazar420 on 2008-02-25
Sorry about the long wait for a reply; I overwhelm myself with my posts querying for help, and then forget about open posts I already have...

Anyway, to answer your question: no. I haven't rearranged any of the shortcut settings, wherever they may lie (the keyboard shortcuts utility doesn't list said feature). As a matter of fact, after several fresh installations, this has yet to change. I am currently sporting the Gateway M520/7000 computer... it is a suspected variant, for I haven't bought it from any retailer, and have yet to find reviews of this M520 with EXACTLY the same specs.

Anyone else know anything about restarting X? Perhaps an added command in the script manager thingy (found in the login window application under 'Menu -> System -> Admin' -> Login Window -> "Edit Commands" button located near the bottom of the first tab'.

P.S. Does anybody know whether I should be loading Xclient script sessions or GNOME sessions as a regular desktop user? I've never noticed that it loaded xclient as default (yet I somehow knew I was using the X desktop whatchama'), and always figured it loaded GNOME session.

---

