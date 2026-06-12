---
title: "Help with UBUNTU installation"
date: 2006-01-04
forum: Desktop Environments
---

### Post by AgonxOC on 2006-01-04
Hello everyone, I am Alex and I am gving Linux a try for the first time. I have a Hard Copy of 5.04, but for some reason it wont install, it gives an error when installing the base. After that I downloaded the CD image of 5.10 and burnt into a CD-RW. The computer wouldnt boot from the disk. I, then, decided to make a bootable disk and that also didnt work. Can someone here help guiding me on making the disk boot and installing the software with not errors.

Thanks

Alex

---

### Post by Sef on 2006-01-04
1) Have you tried the Ubuntu Live CD first to check how well it works on your computer?

2) Did you do an md5sum on the download before you burned it?

---

### Post by constantine on 2006-01-04
are you sure of your iso copy ?
how did you burn it?

---

### Post by AgonxOC on 2006-01-04
No I didnt try the live CD on this particular one. I tried it on my XP machine and it worked. No I didnt do an MD5SUM. How do I do it exactly? I never done it before. Is there a tutorial anywhere I have looked, but have found nothing well written.

Alex

---

### Post by constantine on 2006-01-04
try this [http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by AgonxOC on 2006-01-04
[QUOTE=constantine]are you sure of your iso copy ?
how did you burn it?[/QUOTE]


Yeah its the ISO copy and I just burnt it with Nero..

Alex

BTW the system specs are: AMD Athlon 1700+, 384 MB RAM, 40GB HDD clean and fresh, ECS Mobo. It was an old system I had laying around and I thought I give linux a try.

Alex

---

### Post by AgonxOC on 2006-01-04
[QUOTE=constantine]try this [http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)[/QUOTE]

Thanks, but that didnt help much. Nero nor Explorer gives the options to burn ISO... 

Alex

---

### Post by constantine on 2006-01-04
i was referring to the link which will lead you to this [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)
anyway try to find out here with nero [http://www.weethet.nl/english/cdrw_usingnero_iso.php](http://www.weethet.nl/english/cdrw_usingnero_iso.php)

---

### Post by AgonxOC on 2006-01-04
I think I might have got it right. My Nero is a bit different. CD is burning now. I let you know once I boot the other system...

Alex

---

### Post by AgonxOC on 2006-01-04
Ok so the CD I made worked somewhat... The base installed, but the other files didnt. Well then I rebooted and continued the installation at about 57% I got this:

[722.676339] Buffer I/O error on device hda, logical block 293273

Whats going on here..?

Alex

---

### Post by AgonxOC on 2006-01-04
Guys thanks alot, I finally got it all running. I like it so far now I have to install some drivers...

Alex

---

### Post by keldo on 2006-01-05
Hi Alex

I find my self in a situation very similar to you.
But yesterday I did a successful installation using the free ship it cd.
If you still want to make a functional cd I advise you to try bitTorrent and find another download sources.

hopfully what will work

Martin

---

### Post by BUXjr on 2006-01-05
Smells like a "sketchy" harddrive.  You may want to do a low-level format (factory write zeros) to the disk and try the install again.  See your hard rive manufacturer's website for this type of utility.

If that doesn't work (or at least reveal problems with your HD surface area), perhaps your cdrom drive is getting "tired" and having problems reading from the CD -- although that is NOT what your error seems to indicate (HDA is usually your boot HD "C:\").  Do you have another cdrom (or DVD) drive to attempt the install from?

Just a couple ideas.  You may have already tried these.  HTH.

BUXjr

---

### Post by AgonxOC on 2006-01-05
In my case it wasnt the HDD I dont think.. I was a sketchy ISO copy I burnt in a CD. I grabbed a new CD and burnt a new copy and walla 1 hr later I was messing with linux.

Alex

---

