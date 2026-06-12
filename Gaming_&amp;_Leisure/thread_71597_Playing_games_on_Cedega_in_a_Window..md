---
title: "Playing games on Cedega in a Window."
date: 2005-10-03
forum: Gaming &amp; Leisure
---

### Post by St3althcAt on 2005-10-03
I've recently installed Cedega and successfully installed WoW, but I have a 1280x1024 resolution on my computer and WoW is configured to use 1024x768. When I play the game on Cedega, it goes fullscreen, but the game will only appear on the top left corner of the monitor, leaving the rest of the screen size black (blank). How can I configure Cedega to work on window mode?

Thank you for the attenttion.

---

### Post by jumanji on 2005-10-04
[QUOTE=St3althcAt]I've recently installed Cedega and successfully installed WoW, but I have a 1280x1024 resolution on my computer and WoW is configured to use 1024x768. When I play the game on Cedega, it goes fullscreen, but the game will only appear on the top left corner of the monitor, leaving the rest of the screen size black (blank). How can I configure Cedega to work on window mode?
Thank you for the attenttion.[/QUOTE]

I think you need to edit the config file in cedega(/home/"user"/.transgaming/)
in the file serch for 
; Use a desktop window of the given size
;"Desktop" = "800x600"

To make cedega run games in a window remove the ";" from "Desktop" = "800x600" and in your case make it look like this..

; Use a desktop window of the given size
"Desktop" = "1024x768"

Now it should run in a window in 1024x768...

---

### Post by Luggy on 2006-12-04
I have the exact same problem but that fix did not do anything for me.
Has anyone else solved this problem or had it before?

---

### Post by paulb75 on 2008-01-26
> **St3althcAt said:**
> I've recently installed Cedega and successfully installed WoW, but I have a 1280x1024 resolution on my computer and WoW is configured to use 1024x768. When I play the game on Cedega, it goes fullscreen, but the game will only appear on the top left corner of the monitor, leaving the rest of the screen size black (blank). How can I configure Cedega to work on window mode?

Thank you for the attenttion.

Go to "Edit Settings" (under "Properties" and you'll see a box that says "Desktop" (Default is "No" which means fullscreen). You can choose the screen resolution from there, and it will run it in a window at that resolution. I've noticed though that some games seems to run in a low resolution mode, and higher resolutions result in a tiny corner where the game is displayed. I'm trying to find out how to change that, but I think it's because your desktop resolution does not automatically change to accommodate the games. ;-)

---

### Post by Mike'sHardLinux on 2008-01-26
> **paulb75 said:**
> ...., but I think it's because your desktop resolution does not automatically change to accommodate the games.

I seem to remember this being right, too, paulb. Originally, my xorg.conf only had 1 or two resolutions listed. I added the other resolutions which the games were using, and then they worked fullscreen properly.

I don't know if it makes any difference, but I am using an older version of Cedega, version 5.xx.

edit: I just realized the OP was from 2005!!!! LOL!!!

---

