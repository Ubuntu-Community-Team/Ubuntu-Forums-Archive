---
title: "Nautilus cd writing - multisession possible?"
date: 2005-12-03
forum: Desktop Environments
---

### Post by softgun on 2005-12-03
I have installed Ubuntu Breezy for the first time and am very happy with it. I love Gnome and the whole Ubuntu look!! Everything works for me and the printer was setup in seconds.

Wow!

I then downloaded Puppy linux iso with gwget, right clicked the file and "write to CD" wrote my ISO and it works!

Go -> CD/CVD creator, put 400MB of stuff into the burn/// folder, right clicked on the window and said write CD and it wrote the files to the CD - beautiful!!  But the CD is closed. Almost 200MB wasted :-(

What I want now is to know how to write a multisession CD in Nautilus, and to make this the default.

Could not find an answer in the forums in relation to Nautilus. Nautilus uses cdrecord, therfore this could be set with editing of the /etc/fstab?

Thanks for any help!

---

### Post by savas on 2005-12-03
It seems that nautilus does not support multi-session cds. But you can use X-CD-Roast to burn multi-session cds or run cdrecord from terminal:D

---

### Post by dcstar on 2005-12-03
[QUOTE=softgun]I have installed Ubuntu Breezy for the first time and am very happy with it. I love Gnome and the whole Ubuntu look!! Everything works for me and the printer was setup in seconds.

Wow!

I then downloaded Puppy linux iso with gwget, right clicked the file and "write to CD" wrote my ISO and it works!

Go -> CD/CVD creator, put 400MB of stuff into the burn/// folder, right clicked on the window and said write CD and it wrote the files to the CD - beautiful!!  But the CD is closed. Almost 200MB wasted :-(

What I want now is to know how to write a multisession CD in Nautilus, and to make this the default.

Could not find an answer in the forums in relation to Nautilus. Nautilus uses cdrecord, therfore this could be set with editing of the /etc/fstab?

Thanks for any help![/QUOTE]

You may want to give GnomeBaker or K3B a try.

---

