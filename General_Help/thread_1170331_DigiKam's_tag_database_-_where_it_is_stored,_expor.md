---
title: "DigiKam's tag database - where it is stored, export, backup"
date: 2009-05-26
forum: General Help
---

### Post by kprateek88 on 2009-05-26
My large collection of photos is currently untagged and I was considering tagging it with DigiKam. I'd like to understand where (exactly what file(s) on the disk) DigiKam's tag database is, how it is stored, whether I can easily copy it to another computer if needed, what options I have for exporting the tag data into some plain text format which other programs can read, and so on. Interportability stuff, mainly: what will happen if I move to a different computer or different OS or different photo-managing program.

---

### Post by .nedberg on 2009-05-26
> **kprateek88 said:**
> My large collection of photos is currently untagged and I was considering tagging it with DigiKam. I'd like to understand where (exactly what file(s) on the disk) DigiKam's tag database is, how it is stored, whether I can easily copy it to another computer if needed, what options I have for exporting the tag data into some plain text format which other programs can read, and so on. Interportability stuff, mainly: what will happen if I move to a different computer or different OS or different photo-managing program.

In the root of your album folders you will find a file called digikam.db (IIRC). It is a sqlite database and can be copied to other computers or backed up.

DigiKam can also write the tags to exif-information of the files, so it can be read in any image program.

---

### Post by .nedberg on 2009-05-26
If you are on Jaunty and use digiKam 0.10.0 then the database is named digikam4.db, on earlier version it is named digikam3.db.

---

### Post by kprateek88 on 2009-05-26
Thanks! Yes I should have mentioned that I'm on Kubuntu Jaunty, with DigiKam 0.10.0.

---

### Post by zevans on 2009-05-28
I can confirm photo tags are preserved between Windows Vista and digikam, so the EXIF tag stuff works well.

---

### Post by Pessulus on 2009-07-04
> **.nedberg said:**
> 
DigiKam can also write the tags to exif-information of the files, so it can be read in any image program.

How ?

---

### Post by .nedberg on 2009-07-04
> **Pessulus said:**
> How ?

Not at my Kubuntu/digiKam machine right now. It is somewhere in the settings... Post back if you don't find it and I'll tell you when I am back.

---

### Post by philip5 on 2009-07-08
If you like to try the cutting edge version of Digikam then you could use the packages on my repo for (k)ubuntu 9.04 (jaunty) that holds packages of Digikam 1.0.0 beta 2 (for the moment) among a bunch of other updated packages. 

I love what's going on with Digikam and it surely gives i.e Adobe Lightroom and Bibble a run for their buck! I almost can't wait for Digikam to be in final version even though the beta works pretty well so far and have a bunch of new features and look than the old 0.10.x-version.

The url and instructions on how to use my repo are found below in my signature.

Have fun!

---

