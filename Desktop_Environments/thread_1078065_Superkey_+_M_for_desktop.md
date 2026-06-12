---
title: "Superkey + M for desktop"
date: 2009-02-22
forum: Desktop Environments
---

### Post by amylase on 2009-02-22
Hi everyone,

Using System -> Preferences -> Keyboard Shortcuts I've set up the windows superkey to automatically bring down applications menu. How do I set up the following?

Super + M to clear the desk  
Super + R to open up terminal
(Keyboard Shortcuts doesn't seem to accept Super + another key for some reason).

In addition, how do I set up Control + V for paste while inside terminal?

Thanks very much.

---

### Post by pw_f100_220 on 2009-02-23
If you have intrepid compiz can set up commands really easily.  at the top with general options just go to commands and type the command...such as "gnome-terminal", then go to keybindings below it and specify the key combo.

as for reverting to desktop there is no command for it (i've looked), but someone wrote "wmctrl" so you can type "wmctrl -k on" to show the desktop. that should be apt-gettable (sudo apt-get install wmctrl).  then repeat the key setting with compiz.  if compiz doesn't have it run gconf-editor, go to apps>metacity>keybinding commands to set the command, then global keybindings to choose the key combo.  you'll have to spell the button like this: <Super>m

---

### Post by pw_f100_220 on 2009-02-23
as for terminal paste...you're on your own.  i have trackpoint with the nifty middle click that pastes.  go thinkpads!

---

### Post by amylase on 2009-02-25
Thanks a lot for your help pw_f100_220.

---

### Post by Mazin on 2009-02-25
Ctrl-V sends ^V to the terminal, in the same manner as Ctrl-C sends ^C and Ctrl-D sends ^D.  That's simply how the terminal is expected to work.

Of course, rules can be broken.  In gnome-terminal, go to Edit > Keyboard Shortcuts and set paste.  done.

---

