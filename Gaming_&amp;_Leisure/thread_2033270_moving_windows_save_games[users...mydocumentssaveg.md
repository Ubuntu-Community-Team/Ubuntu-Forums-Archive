---
title: "moving windows save games[users/.../mydocuments/savegames etc...]"
date: 2012-07-25
forum: Gaming &amp; Leisure
---

### Post by zerzu on 2012-07-25
Hello everyone! After spending almost 2 years reading over these forums I am ready to wipe my machine and change to Linux....I have 2 hangups that im curious about before I start and I hope you guys can point me in the right direction as I haven't found a good answer on here, I'm sure its here and if you just link me to it that would be awesome too!
My questions are, when I completely eliminate windows and start using wine where to I put all my saved games from the mydocuments folder to get my games to recognize them?  Also a lot of my games I have in .iso format that I must mount to a "virtual drive" to run them...I am about to start the process now and I have the mydocuments folder backed up.

Thanks in advance guys!

---

### Post by oldrocker99 on 2012-07-25
> **zerzu said:**
> Hello everyone! After spending almost 2 years reading over these forums I am ready to wipe my machine and change to Linux....I have 2 hangups that im curious about before I start and I hope you guys can point me in the right direction as I haven't found a good answer on here, I'm sure its here and if you just link me to it that would be awesome too!
My questions are, when I completely eliminate windows and start using wine where to I put all my saved games from the mydocuments folder to get my games to recognize them?  Also a lot of my games I have in .iso format that I must mount to a "virtual drive" to run them...I am about to start the process now and I have the mydocuments folder backed up.

Thanks in advance guys!

OK, first realize that wine creates a hidden folder called .wine, in which there is a folder called drive_c, which contains a "Program Files" folder. It is possible (I've never tried it) that you can just copy (DON'T move) your Documents and Settings (or whatever) folder to ~/.wine/drive_c/ and see what happens. As far as mounting ISOs goes, there is a terrific equivalent to the much-pirated Alcohol Windows ISO mounter in the repositories called Acetone.

Welcome and do NOT hesitate to ask questions here; that's what this forum is for.

---

### Post by zerzu on 2012-07-25
Thank you!!!! I am now posting from linux and windows is dead!!  I set my swap drive to 10GB is that big enough??  ALso, I installed the nvidia proprietary drivers but my hdmi will not work.....it boots fine to show the Asus logo and it shows the Ubuntu logo then my tv signal dies and it switches to the laptop screen....I own a Asus g74 if that helps anyone.  I am very new to HDMI and how it works with graphics/sound....is this a separate driver I need or am i missing a configuration setting....my TV will not show up in "displays" under settings either also under the system icon under graphics it does not show my nvidia it says unknown...I'm installing updates as I write this so maybe that is the issue?

Thank You!!!

---

### Post by oldrocker99 on 2012-07-26
Dunno about your HDMI problem, which may be a crappy lappy; I do not know. !0 GB for your swap drive should be plenty big enough.

---

### Post by zerzu on 2012-07-26
no...it was me....I had to completely start over today and run everything from the "dash Home" I was trying to do stuff the old fashioned 8.0 way.....apparently I will be using the terminal less and less now it seems....yes? no?

---

