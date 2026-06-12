---
title: "Ugly rendering with GhostScript"
date: 2006-05-24
forum: Desktop Environments
---

### Post by Erwin123 on 2006-05-24
I have a strange behaviour of the GhostScript driver when rendering PostScript. If I view the ps-file with GhostView (gv) or KGhostView the fonts are not as clear as I'm used to from other systems. They are a bit too thin and small characters are smeared. If I view the file from a SuSE machine, everything is nicely legible and smooth (I did X11 forwarding, same monitor, same X11!)

You find three small screenshots appended: two on my Ubuntu Dapper (gv.png and kghostview.png) and one from the forwarded SuSE machine (gv-SuSE.png).

Antialiasing is turned on, gs options in gv are -sDEVICE=x11alpha on both machines.

On the Ubuntu machine, I have gs 8.15.2, the SuSE machine has gs 7.07.1 - this may point to the root of the problem.

Any ideas?
Erwin

---

### Post by Erwin123 on 2006-05-24
It seems that the problem is related to a GhostScript bug which has been introduced with some early 8.x version. I downloaded the recent AFPL version 8.54, built from sources with 

./configure --with-jasper --with-x --with-gs=gs-8.54
make
make install

and set the links 
/etc/alternatives/gs -> /usr/local/bin/gs-8.54
/etc/alternatives/gs.1.gz -> /usr/local/man/man1/gs.1.gz 
(after zipping the manuals)

Finally, you need to tell it about the installed fonts, e.g.
sudo ln -s /usr/share/fonts/type1/gsfonts/ /usr/local/share/ghostscript/fonts

Now everything looks smooth again :-D 
I didn't find a recent Debian or Ubuntu package, although version 8.50 for GPL is out. Somebody should package it!

Cheers,
Erwin

---

### Post by malmjako on 2006-12-16
I just installed the same GhostScript version on Edgy, because I had some troubles with chopped off characters with gs-esp which comes with the system. Now, even though I can view everything just fine with e.g. Evince, nothing prints! I use HPLIP, and it worked fine (except for some characters being chopped off) with gs-esp (v 8.15).

Did you manage to print from your system after installing AFPL GhostScript?

EDIT: After some more tests, it seems only OpenOffice has problems printing with gs-8.54 selected in alternatives. Why, I don't know...

---

### Post by windwalker78 on 2006-12-18
> **malmjako said:**
> I just installed the same GhostScript version on Edgy, because I had some troubles with chopped off characters with gs-esp which comes with the system. Now, even though I can view everything just fine with e.g. Evince, nothing prints! I use HPLIP, and it worked fine (except for some characters being chopped off) with gs-esp (v 8.15).

Did you manage to print from your system after installing AFPL GhostScript?

EDIT: After some more tests, it seems only OpenOffice has problems printing with gs-8.54 selected in alternatives. Why, I don't know...

I just installed gs-esp 7.07.1 on Dapper and everything seems fine including printing locally and via network.

---

### Post by malmjako on 2006-12-22
Installed gs-gpl (Edgy, v 8.50) and everything seems to work fine: no cut-off characters; printing from OpenOffice works. (Not much testing done yet, though...)

---

