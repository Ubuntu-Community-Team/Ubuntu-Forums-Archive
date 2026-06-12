---
title: "A huge problem with my X Server (graphical interface)"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Norppa on 2006-05-31
Something is wrong with my X Server settings. When I start Ubuntu, a blue screen comes, right before the login screen, saying:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" and then options Yes and No. 

My X Window System Version is 6.8.2. Then it says:

"The X server is now disabled. Restart GDM when it is configured correctly." and then it opens Ubuntu in terminal mode only.

Can somebody please help either to configure this X server or to reinstall it (in the terminal). Thank you beforehand!

---

### Post by Ptero-4 on 2006-05-31
Do sudo dpkg-reconfigure xserver-xorg to reconfigure X11 and sudo dpkg-reconfigure gdm to reconfigure GDM.

---

### Post by stiankarlsen on 2006-05-31
If that doesn't work, do ~ sudo nano /etc/X11/xorg.conf, and change the graphics driver to *vesa*

then you will most likely get in, and from there, use easyubuntu or something to install your ati/nvidia drivers.

---

### Post by InsanePenguin08 on 2006-05-31
I encountered this error as well, will let you know if this fixes it.

---

### Post by InsanePenguin08 on 2006-05-31
First I reconfigured both files, but when I reconfigured the GDM I got the error mesasge about the xserver being disabled.

Then I used sudo nano /etc/X11/xorg.conf  and changed the graphics driver to vesa.  After I did that the screen went blank and then my splash came up, but immediately went back to the previous error.

---

### Post by scared_ghost on 2006-05-31
Hi same problem as above,very scared! Just did an update to dapper and i get 
this on reboot. Have to go to bed now but will check back on this tomorrow morning so please if anyone finds a fix that works please post your remedy!
thanks 
regards 
ghost

---

### Post by Sjdoughboy on 2006-06-04
hi all i'm having the same problem i got my other computer working but can not get my main up...

not sure if it is a Dell thing and to add insult this is the first time use Linux....
how do i change it to vesa i'm doing as the text tells me but lost any help world be great...

Newbie

---

### Post by ninjasmith on 2006-06-04
[QUOTE=Ptero-4]Do sudo dpkg-reconfigure xserver-xorg to reconfigure X11 and sudo dpkg-reconfigure gdm to reconfigure GDM.[/QUOTE]

ok i changed my graphics card on my dual boot system.  got the same errors people are descrbing here. I pferformed the above fix and it looks like it has worked (I get the graphical logon screen and no x server error) however after I log on I just get a brown screen and a mouse pointer, no desktop or menus.

I also get the logon sound.

however now nothing is happening, anyideas?

---

### Post by element on 2006-06-05
I did Ptero-4's suggestion and I get the same problem.  I get a message about about the xserver being disabled. Please help!

---

