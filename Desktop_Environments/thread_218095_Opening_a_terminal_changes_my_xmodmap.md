---
title: "Opening a terminal changes my xmodmap?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Eric_T on 2006-07-18
Hello

I've done some changes to the keyboard layout, and when I boot I run "xmodmap usr/share/myxmodmap" and everything works fine. 
But when I open a terminal window, it changes the layout! Anyone knows what's wrong?

---

### Post by kabus on 2006-07-18
What kind of terminal, a virtual (CTRL-ALT-F1) one or a terminal emulator like Gnome-Terminal ?
The former isn't affected by xmodmap. 
If the problem occurs in the latter does it change the keyboard layout globally or only in the terminal? Any particular keys affected?

---

### Post by Eric_T on 2006-07-18
The latter, opening a Gnome-Terminal. It changes the layout globally. Don't know about particular keys, but I've swapped Caps Lock and Ctrl, and it swappes them back, that's the main problem.

---

### Post by kabus on 2006-07-18
> **Eric_T said:**
> The latter, opening a Gnome-Terminal. It changes the layout globally.


Check ~/.bashrc and ~/.bash_profile for xmodmap commands.

---

### Post by Eric_T on 2006-07-18
It's only the xmodmap command that I put there to make it run on boot... 
But somehow, adding the line a second time as well fixed the problem.. werid.
Anyways, thanks for the help :)

---

