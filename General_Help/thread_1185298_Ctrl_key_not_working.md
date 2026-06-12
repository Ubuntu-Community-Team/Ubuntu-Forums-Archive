---
title: "Ctrl key not working"
date: 2009-06-12
forum: General Help
---

### Post by kvanaken on 2009-06-12
I have installed Jaunty Netbook Remix on an old Thinkpad R52, with a Belgian keyboard layout (azerty, some difference in where & and so on are located).  Now, the Ctrl keys do not seem to work as expected.  Specifically, LCtrl-C in the terminal does nothing (no new line, can't kill programs), while RCtrl has no effect at all.

I have tried various keyboard layouts, currently using Generic 102 (Intl) with Belgian layout.  All other keys seem to work fine, it's just the Ctrl keys that act up.
I have checked what happens when pressing Ctrl-C using xev.  The LCtrl key press is seen, but then pressing c while holding LCtrl gives no new event.  The RCtrl key press is not seen at all by xev.  Interestingly, Ctrl-D does give the expected result (EOF in cat).

I have also tried rebooting in console (so no X running).  This gives the same results as above (so LCtrl-C does not interrupt any programs, RCtrl does nothing).

Any hints on what could be wrong would be appreciated.

---

### Post by dk_learning_linux on 2009-06-12
Just check the "keyboard shortcuts" option in your terminal window. open terminal 

edit > keyboard shortcuts. I think this may help you .

---

### Post by kvanaken on 2009-06-12
I have already checked the terminal shortcuts.  The copy and paste options are the standard Ctrl+Shift+C and Ctrl+Shift+V.  There are also no other options which would conflict with standard Ctrl-C behavior.  
I would be a bit surprised if the standard Ctrl-C terminal functionality was by default overridden, though I guess it might make sense on a distribution aimed at netbooks.

---

### Post by dk_learning_linux on 2009-06-12
I am not familiar with ubuntu netbook remix. 
Whether other ctrl key combinations working in the terminal?

---

### Post by kvanaken on 2009-06-17
After some further investigation, it looks like the keyboard itself is broken.  There is still the chance that the BIOS itself captures the keystrokes before they are sent to the kernel, but the BIOS used to work, and was not changed recently.

---

