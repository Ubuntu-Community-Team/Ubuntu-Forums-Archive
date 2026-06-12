---
title: "Rdesktop or terminal server mouse pointer disappear"
date: 2008-06-26
forum: Desktop Environments
---

### Post by heraths on 2008-06-26
Hi friends,
I tried to connect to university machine which runs windows xp through terminal server client and rdesktop. I could connect but once connected mouse pointer disappears only in that window. I can't see the mouse pointer arrow sign on that window. Outside that window mouse pointer is available. 
I am using 8.04.
Any suggestions.
Thank you,

---

### Post by lisati on 2008-06-26
My experience of remotely accessing a Windows machine is through Gnome-RDP. It has as one of its options a choice between "Viewer only" (meaning look but don't touch) and "Control remote host". Perhaps there's a similar option in the software you're using that has somehow gotten itsself into the equivalent "viewer only" mode.

---

### Post by heraths on 2008-06-26
Thank you very much for the response.
However even though mouse pointer is invisible, i can see the button visual effect changes inside the window. For example, when i move the mouse inside that window, button color changed etc and   then i recognize mouse pointer is there. Then i can click on that and continue. So i think that is not a kind of 'View Only' setting.
However I ll try to install Gnome-RDP and give a try.

---

### Post by heraths on 2008-06-29
I face the same problem with Gnome-RDP.

---

### Post by krtica on 2008-10-23
I have the same problem. I can't see mouse pointer during rdesktop session from my ubuntu 8.04 laptop (FSC Amilo Pro V3515) to Server 2003.
I also can see mouse movement consequences, but not the pointer.
Does anyone have any ideas, please?
:(

---

### Post by krtica on 2008-11-01
Ok, i solved my problem. Maybe it will help someone.
I think that roblem was with VIA Chrome9 graphic card on "vesa" driver.
I installed "openchrome" drivers ([https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")) and now i can see 1/2 of pointer. :D

---

