---
title: "System Bell &amp; XFCE"
date: 2007-04-05
forum: Desktop Environments
---

### Post by tjayluke on 2007-04-05
First post here.

Anyways, just recently switched to using XFCE on Ubuntu Edgy. In Gnome I had the system bell turned off since it was getting annoying when searching in firefox and getting a bell at every search character if nothing was found. In XFCE I'm now getting the same system bell, so the setting has obviously not carried over. 

I've been looking for a way to turn this off, but I haven't found anything in the menus anywhere, and I haven't found anything via google-fu or forum search either. Anyone have any advice?

---

### Post by fribacka on 2007-04-22
Edit or create the file ~/.inputrc, add the line ```
set bell-style none
``` and restart bash or the hole session. Otherwise, execute the command ```
 $ xset b off. 
```I don't really know what the latter and if the setting is permanent. Perhaps you can add the line in ~/.xinitrc.

---

### Post by timhodkinson on 2008-05-14
For a permanent fix, I went to the Menu/System Settings/Autostarted Apps and clicked on "add" and put in the above command, "xset b off" and clicked on OK, and restarted the XFCE session.

Now it's automatically run everytime a session starts and the bell is gone.

---

