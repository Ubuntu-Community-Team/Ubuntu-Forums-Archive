---
title: "Installation Problem with CD2"
date: 2006-07-06
forum: Gaming &amp; Leisure
---

### Post by Cris987 on 2006-07-06
I am sure this problem has bugged others as well, but i have googled and searched to no avail.

I'm trying to install MVP Baseball 2006 with wine. Everything is good and fine until the installer asks for CD2. First of all, I cannot eject my dvd rom by pressing the hard physical "eject" button on my rom NOR by right clicking on the drive in and clicking "eject" on desktop. I searched and found somewhere the command "wine eject d:". The CD ejected, and I inserted my second CD and put in terimanl "mount /media/cdrom0" but terminal says it's busy or that it's already mounted etc. 

How can I get around this? Thanks in advance.

---

### Post by K.Mandla on 2006-07-06
I'm not sure this would work at all and I might be off track, but the first idea that comes to mind is to make ISOs of the discs. Then you could mount or unmount each one as needed. Would that work?

---

### Post by Cris987 on 2006-07-06
[QUOTE=K.Mandla]I'm not sure this would work at all and I might be off track, but the first idea that comes to mind is to make ISOs of the discs. Then you could mount or unmount each one as needed. Would that work?[/QUOTE]

I found the same solution in another forum, but I can't figure out the command to mount the .ISO's. Any clue?

---

### Post by DoktorSeven on 2006-07-06
Usually mounting the CD without being inside the physical directory, then giving Wine the full path to the installer, will allow you to unmount CD1 and mount CD2:

[b]mount /media/cdrom
wine /media/cdrom/setup.exe[/b] (or whatever it's called)

If this doesn't work, you can mount ISOs with:

**sudo mount -t iso9660 -o loop cd1.iso /media/cdrom**

---

### Post by thom_raindog on 2007-10-06
uhm.. I ran into the same problem with MVP 2003.

How do I create an iso again? :)

---

