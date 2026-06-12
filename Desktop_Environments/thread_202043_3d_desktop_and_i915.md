---
title: "3d desktop and i915"
date: 2006-06-22
forum: Desktop Environments
---

### Post by isenalim on 2006-06-22
Hi,
I'm quite new to linux and ubuntu. I wanted to try 3ddesktop. Typing 3ddesk in a terminal gives me this error

Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.

My graphic card is reported to be

Mobile 915GM/GMS/910GML Express Graphics Controller

I have an hp Pavillon laptop.

As far as I understand, it is a problem of lack of opengl drivers, but I don't know how to proceed.

Thank you for any help

Bp

---

### Post by Test33 on 2006-06-23
I'm getting this error also on my desktop my video card is a 5200 GeForce.

---

### Post by Test33 on 2006-06-23
I fixed it for me. Just follow the steps at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) and everything worked.

---

### Post by threethirty on 2006-06-23
try looking for the driver on intels site, i found a .rpm and the used alien to make a .debout of it and it worked for me.  I have a compaq V2000 and it has the same friggin' chipset.  And good luck with the intel site, it was a bear for me to find anything.  if you cant find it, pm me your email addy and I'll send you a link to the .deb I made

---

### Post by isenalim on 2006-06-26
Ok, thanks, I will have a look at the intel website.

---

### Post by isenalim on 2006-07-02
Hi,
in the end it works! I just edited the xorg.conf file and tell him to use the "i810" driver instead of "vesa" in the device section.  The correct driver was installed but unused... this seems like a little bug of Dapper. X is pretty faster now.
Bye

---

