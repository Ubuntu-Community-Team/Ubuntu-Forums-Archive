---
title: "Acessing my drive"
date: 2009-02-22
forum: General Help
---

### Post by SanctusMessor on 2009-02-22
Recently Vista killed over on me, no surprise but I still need to recover the data. Normally I'd just boot into Ubuntu and grab the files, but it is telling me that it is unable to mount the drive. I also have tried in Kubuntu (both are 8.10) and it said something along the lines of "The operating system did not shut down properly, unable to mount." or something to the effect. Vista repair from the disc isnt working, not like I expected it to or anything, but it was worth a shot. Its sad, I dont want to lose all the work I had there, normally its all backed up but havent backed for 2 weeks. 

On a side note, anyone have a good solution for maybe a linux box that I would store away in the closet and have my vista, or a certain folder within vista, back up all changes automatically?

Thanks

---

### Post by taurus on 2009-02-22
Can you at least force mount it?  Which partition is your vista?

```
sudo fdisk -l
```

---

### Post by Hobgoblin on 2009-02-22
When it fails to mount it gives you the command you need to mount it using the force option.  This will force the partition to mount.

---

### Post by banjo man on 2009-02-22
yeah, when an ntfs volume doesn't get properly unmounted from windows, the linux drivers are careful not to do anything to damage the fs...

---

### Post by SanctusMessor on 2009-02-22
This is the message I get out of it :X

[IMG]http://i95.photobucket.com/albums/l147/lyricaray/desktopcopy.jpg[/IMG]

---

