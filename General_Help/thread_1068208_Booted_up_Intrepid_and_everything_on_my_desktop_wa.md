---
title: "Booted up Intrepid and everything on my desktop was GONE!"
date: 2009-02-12
forum: General Help
---

### Post by faceless-21 on 2009-02-12
Hey guys like the title says, I booted up Intrepid early this morning and everything on my desktop except for the Icon for a DVD and then a movie that I had loaded from a SD card last night(thankfully since I dont know if the person who recorded it saved it)
  I before turning off my laptop(Dell Inspiron 9300) the only thing I did was delete a couple things to make room for the .avi file and browse the web maybe for a sec.  Any ideas on what happened?

  Thanks for any help you can give!

---

### Post by faceless-21 on 2009-02-12
bump...?

---

### Post by hikaricore on 2009-02-12
Please check your trash and your home folder, it is entirely possible that you deleted some files by accident or moved them without knowing.

Things just don't disappear for no reason so unless someone else has access to your system or your hard disk is damaged this is probably the case.

---

### Post by faceless-21 on 2009-02-12
Yeah I checked my home folder and my trash.  Nothin. Any data recovery software anyone suggests?   Freeware being what I am looking for :D

---

### Post by faceless-21 on 2009-02-13
Bump...?

---

### Post by solwic on 2009-02-13
> **hikaricore said:**
> Please check your trash and your home folder, it is entirely possible that you deleted some files by accident or moved them without knowing.

Things just don't disappear for no reason so unless someone else has access to your system or your hard disk is damaged this is probably the case.

Actually I've had icons that I'll add to my panel, set their icon, and then when I reboot they're gone.  When I add them back, two of the icon shows up; the one I added, and the one that had disappeared.  

Maybe this has happened to the OP?  Try adding back an icon or something that is missing and see what happens.  

I don't have any clue what causes that, but it does happen from time to time.  

Good luck!

---

### Post by faceless-21 on 2009-02-13
Its not just icons...  It was photos and other items...  When I first turned on the computer I could see the wallpaper for an instance(which is one of the things that got deleted) and other icons, but then as it started to load up they disappeared.  So I then checked the trash and my Home folder but there was nothing...  Does anyone have any data recovery programs they suggest for linux?

---

### Post by faceless-21 on 2009-02-14
Anyone...?  Anyone...?  Noone...?  Data recovery software?

---

### Post by bryncoles on 2009-02-14
photorec and test disc - they're the same software, and they're in the repos. you'll need an external drive at least as big as the one you're attempting to recover, and theres good walkthroughs for using each on the homepage:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

*edit*

ah yeah, and dont use the drive you lost data from at all for anything until you've recovered your data, as the more you use it, the less data you will be able to recover.

---

### Post by manuelg on 2009-02-14
Did you check your Desktop folder ?

/home/yourname/Desktop

---

### Post by faceless-21 on 2009-02-14
> **manuelg said:**
> Did you check your Desktop folder ?

/home/yourname/Desktop

yes I did.  nothing

---

### Post by manuelg on 2009-02-14
Go to safe mode, and do a chkdsk on the volume.  If it is corrupted perhaps the files will be recovered and place in a root folder called lost+found.

---

### Post by faceless-21 on 2009-02-15
> **manuelg said:**
> Go to safe mode, and do a chkdsk on the volume.  If it is corrupted perhaps the files will be recovered and place in a root folder called lost+found.

  Tried that and checked the lost+found and there is nothing....  I have Virtual Box installed and I think I have it set to expand its drive when needed.  Could it be that I had a small amount of room left on my hard drive and I booted it up and it kinda expanded its way over the desktop files?

---

