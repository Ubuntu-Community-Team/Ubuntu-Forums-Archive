---
title: ".bash_profile"
date: 2005-04-07
forum: Desktop Environments
---

### Post by theChauvinist on 2005-04-07
Sorry, I had no idea where to post this so feel free to move it...

Anyway, I've just started learning shell scripting, and am editing the .bash_profile file, which I've read on a multitude of sites loads on startup. This doesn't seem to be the case, as any changes I make to it don't change a thing, even when I completely reboot.

I've added the line

alias today='date +"%A, %B %-d, %Y"'

as a test. If I use the command 'source .bash_profile' then the change takes effect, but if I log out and log in again, It doesn't work. 

Please help, it's been going so well up to now!

---

### Post by Leif on 2005-04-07
You can try putting it in .bashrc instead.

---

### Post by theChauvinist on 2005-04-07
[QUOTE=Leif]You can try putting it in .bashrc instead.[/QUOTE]
 Works like a charm, thanks!

Do you know why .bash_profile isn't used? Is it disabled in Ubuntu or is it something else?

---

### Post by cwaldbieser on 2005-04-07
.bash_profile is only executed from a login shell.  Try hitting CTRL-ALT-F1 and switching to a virtual console and logging in that way to see if your .bash_profile takes effect.

---

### Post by theChauvinist on 2005-04-08
Once I've pressed Ctrl+Alt+F1, the gnome-session command won't start the GUI, it gives the error:

(gnome-session:16270): Gtk-WARNING **:cannot open display:

Any ideas?

---

### Post by beesee on 2005-04-09
X is already running, just hit Alt-F7 to go back

---

