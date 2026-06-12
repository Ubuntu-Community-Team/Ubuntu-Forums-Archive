---
title: "Question regarding CD-writing with Nautilus"
date: 2006-01-01
forum: Desktop Environments
---

### Post by ubuntuuser on 2006-01-01
When I insert an empty CD-R, nautilus lets me copy data on that CD without using any additional programs like gnomebaker etc.
There is one annoyance. Before writing the data to the CD, nautilus or whatever program nautilus uses to burn the data, creates a CD image, which I don't want because it slows down the burning process and temporarily uses space on my HDD that I don't have. Furthermore, the data already IS on my hard drive, so I don't understand the reason for this step. I could accept it if I was copying another CD directly, but not if I'm simply copying data from my HDD. How can I get nautilus to burn CDs without creating an image first?

---

### Post by encompass on 2006-01-01
The best and safest way to burn and image is to make the image first.
Imagine if the data had changed in the middle of a burn.  Taht wouldn't be very nice now would it.  I am sure there may be a way; but personally, it is 600 mb of data that you won't need to wory about in 30 minutes cause it deletes it anyway.;) 
If you want to get more burning features, then the jsut works nuatilus cdburner, I would try gnomebaker.

---

### Post by hajk on 2006-01-01
Files aren't just burnt to CD, since there is no receiving file system already waiting... making a CD iso image is therefore a necessary step. Two programmes that can be used in tandem are: "mkisofs" for the image, and "cdrecord" for burning it to disk. Popular CD-burning programmes are often just front-ends to these.  

It is not necessary to put the 600+ MB image on the hard disk, because the output from "mkisofs" can be piped straight into "cdrecord" -- one of the niceties of the UNIX world. The man-page for cdrecord gives the following example:

mkisofs -R /master/tree | cdrecord -v fs=6m speed=2 dev=2,0 -

where /master/tree is the absolute path to the directory that you want to put on the CD, and don't forget the hyphen at the end. The meaning of the options can be checked in the same man-pages -- you can omit the speed option (cdrecord will pick one based on the perceived quality of the blank CD);   and the dev can be checked by running cdrecord first with the -scanbus option. If your drive is an ATAPI device, then check the README in /usr/share/doc/cdrecord.

Don't worry: you need to check all this only once, the findings can be used for all future CD burns. You might even collect all of this in an executable script.

---

### Post by ubuntuuser on 2006-01-01
Thanks hajk, your answer explains a lot to me. The original problem is solved, but just for understanding:

A blank CD-R has no filesystem on it, therefore I need to create an image before writing on it. What about an already used CD-RW? Let's say I blanked it, is it without a filesystem again or is there some kind of FS on the CD because it has been used before? Would I still need to create an image?

---

### Post by hajk on 2006-01-01
Blanking a CD-RW is just that, so you must again create an iso image in order to write to that disk.

Now, you'll note from the cdrecord man-page that a "multi-session" CD can be burnt -- this allows files to be added to a CD burned earlier. This is only possible if the CD has not yet been "closed", so not really of much use in practice unless you aren't able to collect all the files in one go. Once the CD has been "closed" (or fixated), that's it -- you can't add any more files. But then, who cares nowadays with a 100-blank spindle costing less than 20 euros (or dollars).

---

### Post by ubuntuuser on 2006-01-01
Thanks a lot.

---

