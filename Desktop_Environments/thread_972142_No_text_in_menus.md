---
title: "No text in menus"
date: 2008-11-05
forum: Desktop Environments
---

### Post by atomic450 on 2008-11-05
ubuntu 8.10 w/kubuntu desktop 

kmymoney has no text in menus. It looks like text is behind menu box, knetworkmanager also has the same problem. Anyone ran into this before?

K3b also has same problem...
Happens in gnome or KDE4

Thanks

---

### Post by BJRhodes on 2008-12-13
I had exactly the same issue and found a fix on a forum. Now I can't find it again after a reinstall and I have the same issue again! I think I wrote it down so if I find it I'll post it.

Basically the solution was to add a line to your xorg.conf enabling the driver to work through all menus, something like option "forgotten"="1"

Anyone know the line I've forgotten?

---

### Post by BJRhodes on 2008-12-13
Got it, I did write it down.

I'm using an Nvidia 7500GT and driver -96 on KDE4.1 Kubuntu intrepid. Someone suggested I add a line to the xorg.conf file and it worked.

In the section device add the line Option "RenderAccel" "0"

Fixed for me.

---

### Post by vom357 on 2010-10-16
was there NO text or was it just "grayed out" non-functional?
i can see the text in the boxes but it wont be active

---

### Post by kio_http on 2010-10-16
@ above. It is advisable to start a new thread with details. After all this is an old thread and it concerns Kubuntu Intrepid which is outdated.

---

