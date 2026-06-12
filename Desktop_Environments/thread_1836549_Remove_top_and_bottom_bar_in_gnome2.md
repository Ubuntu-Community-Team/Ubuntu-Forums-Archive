---
title: "Remove top and bottom bar in gnome2"
date: 2011-08-31
forum: Desktop Environments
---

### Post by BK Baal on 2011-08-31
I'm running Ubuntu 11.04 (Ubuntu classic), i would like to know if there's an option that could allow to enable\disable the top and bottom bar, or at least hide them, so to show the entire desktop and run commands from the terminal.
Thanks in advance.

---

### Post by madjr on 2011-08-31
something like this?
[http://wawan-kurniawan.web.id/how-to-remove-gnome-panel-in-ubuntu-10-10/](http://wawan-kurniawan.web.id/how-to-remove-gnome-panel-in-ubuntu-10-10/)

---

### Post by BK Baal on 2011-08-31
> **madjr said:**
> something like this?
[http://wawan-kurniawan.web.id/how-to-remove-gnome-panel-in-ubuntu-10-10/](http://wawan-kurniawan.web.id/how-to-remove-gnome-panel-in-ubuntu-10-10/)
Thanks for the reply.
I tried, but it appeared only one file in the configuration editor.
Looking at the comments, i tried to browse to  /usr/share/gnome-session/sessions/
And found some files, one was named classic-gnome.session.
I've made a backup copy on desktop, then deleted it. When i logged back in, it appeared a xorg dialog saying "no session found" and only the desktop appeared, without icons and without background image. I couldn't even open the terminal, so i've entered in the recovery console and restored the file.

Maybe i didn't explained it well, i want to use the Gnome windowed terminal. Even if icons remains is ok, i want only the two bars to disappear.
Looking at the panels option there's an autohide option, but it still show it a bit. Also i can't set the panel height lower to 21 px.
Coming thinking of it, i could also delete the panels. But then, i don't know how to restore them...

---

### Post by madjr on 2011-08-31
you could delete 1 and just keep 1

there are also guides that show how to restore them

---

### Post by Enigmapond on 2011-08-31
> **madjr said:**
> you could delete 1 and just keep 1

there are also guides that show how to restore them

OR

Delete both of them and use AWN ...:)

---

### Post by madjr on 2011-08-31
> **Enigmapond said:**
> OR

Delete both of them and use AWN ...:)

and/or gnome-do , synapse or kupfer :)

---

### Post by Enigmapond on 2011-08-31
> **madjr said:**
> and/or gnome-do , synapse or kupfer :)

Gotta LOVE Ubuntu. Try customizing in Windoze and you appreciate the "Be what you want to be" attitude you have with this OS...(Synapse Rules...BTW..)

---

### Post by Krytarik on 2011-08-31
True about AWN and Synapse! :D

See this guide on how to set up a Gnome-Panel-free session, whichever alternative you choose:

[http://www.tuxgarage.com/2011/05/run-awn-dock-in-natty-narwhal.html](http://www.tuxgarage.com/2011/05/run-awn-dock-in-natty-narwhal.html)

Greetings.

---

### Post by BK Baal on 2011-09-01
Apparently, i can't delete all the panels (at least one of them must be open). However, i'm looking forward to AWN and Synapse!

Thanks to everyone for the help!

---

### Post by drawkcab on 2011-09-01
openbox + hotkey to terminal

---

