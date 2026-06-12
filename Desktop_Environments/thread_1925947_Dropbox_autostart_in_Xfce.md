---
title: "Dropbox autostart in Xfce?"
date: 2012-02-15
forum: Desktop Environments
---

### Post by M1ke on 2012-02-15
I'm currently experimenting with Xubuntu and the final hurdle to overcome before I can adopt it on  all my machines is dropbox integration. A search of the dropbox forums turned  up some excellent instructions for downloading and installing dropbox in a  non-gnome environment, and I can run the app and link the computer to my  account etc.


 The one thing I can't seem to get it to do though is autostart the  application on boot! If I run the command "~/.dropbox-dist/dropboxd"  from the terminal the app starts and begins to sync, but if I close the  terminal window the app terminates too.


 I've added a new entry to my startup applications with the command  "~/.dropbox-dist/dropboxd", but it never autostarts. Is there something  else I need to do?

---

### Post by LewisTM on 2012-02-15
Autostart commands don't recognize things like ~ or $HOME, those are shell shortcuts.
So just use the full path to dropboxd. Alternatively, you can specify a shell command like [FONT="Courier New"]sh -c "~/.dropbox-dist/dropboxd"[/FONT] and that will work.

Cheers!

---

### Post by M1ke on 2012-02-15
[FONT=Courier New]sh -c "~/.dropbox-dist/dropboxd"[/FONT] [FONT=Arial][SIZE=2]has [/SIZE][/FONT]fixed the issue, thanks for your help! I'll remember that.

---

