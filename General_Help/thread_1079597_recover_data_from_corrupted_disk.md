---
title: "recover data from corrupted disk"
date: 2009-02-24
forum: General Help
---

### Post by Green_Star on 2009-02-24
Hi,

One of my internal hard drive(not bootable) was some how corrupted, I tried fixing it by running fsck but it taking longer time(I ran for two days but still didn't finish), and funny part is I can not run fsck when I booted into Ubuntu, whole system just hangs, so need to hard reset the system, I have to run fsck by booting using live disk. So what I am thinking is, to use any data recovery software, I need very little data from that disk, rest of is almost use less. So what software you recommend? any GUI based recovery software? I would like to recover by directory names(I didn't remember some of the directory names?).

Thanks in advance.

---

### Post by Green_Star on 2009-03-03
Bump

---

### Post by kilroy423 on 2009-03-03
If you can boot into a live cd, why don't you just mount the partition and grab your data?  I don't see why you wouldn't be able to grab the data.  If you need some forensic software...there is tons out there.  I have used scalpel([http://www.digitalforensicssolutions.com/Scalpel/](http://www.digitalforensicssolutions.com/Scalpel/)) before and it was pretty easy.  Good luck!

---

### Post by khelben1979 on 2009-03-03
I did a search on sourceforge.net and found [these 2 programs]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=787") which might be of interest.

Other than that, if you decide to extract files from that harddrive from a Windows enviroment, then I'm sure you'll find a lot of software. Just googling I saw a lot of stuff, although I'm uncertain how well they can handle the Linux file system. I guess it depends on how powerful the software is and in many cases I think you need to pay some money to get something powerful, I guess.

[SpinRite]("http://en.wikipedia.org/wiki/Spinrite") is supposed to be a powerful program for fixing harddrives, however I'm uncertain if it is what you're looking for.

---

