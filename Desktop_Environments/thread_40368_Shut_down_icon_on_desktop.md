---
title: "Shut down icon on desktop?"
date: 2005-06-08
forum: Desktop Environments
---

### Post by James_Black on 2005-06-08
How can I place the "LOG OUT" icon on the desktop?

---

### Post by BimberiDreamer on 2005-06-08
Hi James,

You can place one on a Panel as follows:

  Right Click on Panel
  Select "Add to Panel..."
  Scroll down to the "Log Out" item
  Click "Add"

Hope this was what you wanted.

Cheers, Dave.

---

### Post by James_Black on 2005-06-09
Thanks Bimberi, but isn't it possible to place that icon just on desktop and not on the panel?

---

### Post by BimberiDreamer on 2005-06-09
Hi James,

Hmm - I see what you mean.  It doesn't let you drag it onto the desktop.

A (somewhat kludgy) alternative is to create a Launcher, by right-clicking on the desktop, with these properties:

  Name: Shutdown
  Command: sudo shutdown -h now
  Type: Application
  Run In Terminal: checked

It's doesn't work as nicely though - a terminal window appears and prompts you for your password (for the "sudo").  Somehow the panel applet is getting around the restriction that only root can initiate a shutdown.

Anyway, HTH.

Cheers, Dave.

---

### Post by James_Black on 2005-06-09
That sucks! Because I wanted to place that icon on my "Guest" account. :( Thanks anyway.

---

### Post by Alexander Kirillov on 2005-06-09
[QUOTE=James_Black]How can I place the "LOG OUT" icon on the desktop?[/QUOTE]
 Create a launcher as described in BimberiDreamer post (except that you do not check "run in terminal" option), but put the following line as command: 
gnome-session-save --kill

---

### Post by James_Black on 2005-06-09
Thanks! It's working now! :)

---

