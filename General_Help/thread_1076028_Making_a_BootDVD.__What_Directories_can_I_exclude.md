---
title: "Making a BootDVD.  What Directories can I exclude?"
date: 2009-02-20
forum: General Help
---

### Post by garyflynn on 2009-02-20
After going back and forth between Ubuntu and Windows several times, I consider myself still a newbie to Ubuntu.

I am now attempting to make a bootdvd from my current installation.  Much as I wish there was a gui, there does not seem to be one, so I'll be editing bootcdwrite.conf, especially the NOT_TO_CD= section.

My Ubuntu partition now uses a little more than 5 gigs, so I'll have to get rid of almost a gig to fit it onto a dvd without bothering with compression.

I know already that I'll exclude my mounted data storage disks where I keep my music collection.

I've updated kernels, and have 100 megs worth of old kernels and modules, older than the one I currently boot. Can I exclude them and their related files, or are they somehow referenced or necessary to my current installation?

Where are there temp files that I do not have to include on a bootcd? I don't mind losing things like my Mozilla favorites, but I don't want Firefox crashing because an entire directory has not been created.

But are all the software packages I've installed kept anywhere that can be excluded from the bootdvd?

I'd appreciate as comprehensive help as possible in creating my bootcdwrite.conf file, especially in delineating the files I do not want that are in my ubuntu partition but that I do not want on my bootcd.  Whatever has no functional meaning but takes up space.

Thanks very much in advance.

---

### Post by garyflynn on 2009-02-21
1 question.  When I upgrade kernels and go from 2.16.19 to 2.16.23, there are still about 50 megs of files related to 2.16.19 on my system.  (IIRC, Maybe my numbers are wrong).

Can I delete the files related to 2.16.19? Or does my system somehow still need them?

---

### Post by garyflynn on 2009-02-21
2 questions:

Is there a general way to tell a temp file from one that is necessary for a system to run in ubuntu?  Are there any files/folders that take up space but that can be safely deleted after a reboot or something?

---

