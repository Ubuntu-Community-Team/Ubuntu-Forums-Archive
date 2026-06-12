---
title: "Ubuntu 8.04 Gnome panel fails to load at boot"
date: 2009-04-07
forum: Desktop Environments
---

### Post by twgray on 2009-04-07
I have just installed the latest updates to Ubuntu 8.04 and now, most of the time, Gnome Panel fails to load at boot-time.  Sometimes, by restarting X (Ctrl-Alt-BS) I can get it to load, and sometimes not.  How can I restart it from the command line without restarting X, or rebooting?  And, more importantly, does anyone have a clue as to why it wouldn't load in the first place.  dmesg gives no clues.

Help...and thanks in advance.

---

### Post by ajgreeny on 2009-04-07
Either simply ```
gnome-panel
``` in terminal or in run dialog box (Alt+F2) will start it if is not running, but I can't imagine why it isn't doing it automatically some times when you boot.

---

### Post by twgray on 2009-04-08
As it turns out, gnome-panel is running, it is just not visible.  If I kill the process and start gnome-panel again, it shows up.  Any ideas as to what would cause g-p to not be visible after a boot?

---

### Post by ajgreeny on 2009-04-08
Is it set to autohide?  Right click somewhere in an empty panel space and choose Properties.  Uncheck the Autohide button if it is selected, and you may be OK, but it does seem odd, I must admit, for it to the appear when restarted.

---

