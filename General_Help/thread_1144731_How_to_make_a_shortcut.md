---
title: "How to make a shortcut?"
date: 2009-05-01
forum: General Help
---

### Post by jigglywiggly on 2009-05-01
I know this seems simple and it probably is but I'm confused.

Ok to make a short I right clicked my desktop and create a launcher

Name: SRB2 (Sonic robo blast 2)

Command: "wine "/home/jigglywiggly/.wine/dosdevices/c:/Program Files/SRB2/srb2win.exe"

When I launch it it says SRB2.SRB/SRB2.WAD not found! Expected in Y:\, ss files: Y:\\srb2.srb and Y:\\srb2.wad

Why is it it expecting it in the Y directory? When I am in the C: directory?(Wine partitions obviously)

I'd really appreciate some help, I remember I had this problem before, to fix it I just dumped the files form C: to Y: but I want to know a better solution, that is really messy.

---

### Post by linuxuser21 on 2009-05-01
You might be making this more difficult than it needs to be.  lol.  You can go Applications> Wine >Programs find the app you want an drag it to the desktop.
As for the "Y" directory, the only thing I can think that it would be is the dive mapping.  Applications> Wine> Configure Wine click on the Drives tab at the top and there is your drive mappings.

---

