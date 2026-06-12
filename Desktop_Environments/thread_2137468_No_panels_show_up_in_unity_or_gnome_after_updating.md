---
title: "No panels show up in unity or gnome after updating some software."
date: 2013-04-20
forum: Desktop Environments
---

### Post by RefinedCode on 2013-04-20
Before updating to Raring I updated everything else on ubuntu 12.10, after i rebooted my computer everything loaded except the unity panels, I could open a terminal with Ctrl+Alt+T, but the window decorations did not show up.  When I typed unity --replace into the terminal I got the following message:

> unity-panel-service : no process found  

I tried many things related to unity, including a complete purge and install of unity and compiz, this still gave me no panels.  the only thing I see when log into my computer are the desktop icons.  I didn't want to spend all day trying to get unity to work, so I decided just to put gnome3 on (wasn't on my computer before, I did a fresh install of all the gnome3 packages) and use that instead.  The login window of gnome3 works fine, but just like with unity, there are no panels or window decorations, just desktop icons.  OpenGL and any 3d Wine games working fine, I can launch portal 2 or minecraft from the terminal so I dont think its related to my graphics drivers.

Does anyone know what might be wrong here?  Or is there more information I can give here to help me get gnome3 or unity working?  I prefer unity, but since any desktop environment I try isnt working I know it cant be related to that.  

Also this might be unrelated but no icons show up in ccsm, just a bunch of check boxes.

Thanks for any help!

---

### Post by jmcgee on 2013-04-24
I updated 12.04 yesterday and I think I have same problem. No menus in gnome, cinnamon or unity. I do have desktop icons and background. Did you get your problem resolved?

---

### Post by jmcgee on 2013-04-25
And I have solved my own problem. I have to connections to my TV from the Acer Revo. DVI>HDMI adaptor and VGA.  I was watching the HDMI input that had no menus.  Once I switched to VGA input, I had menus.  Apparently, the xorg.conf file got borked on update, and I restored a backup I had made.  Now menus on both DVI and VGA outputs.

---

