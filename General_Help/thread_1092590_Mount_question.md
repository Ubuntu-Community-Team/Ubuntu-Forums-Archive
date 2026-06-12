---
title: "Mount question"
date: 2009-03-10
forum: General Help
---

### Post by prow on 2009-03-10
I apologize in advance for the noobness of this question but i couldn't find the answer anywhere as i have no idea what im looking for.

I noticed my Vista Partition and my external HDD automatically mount and place an icon on my desktop.  I opened up fstab and can see the entry for the vista partition but not for the external drive.  I wanted to change the mount point and also the name for the vista partition so i created a new folder in /media called VistaOS then changed the fstab entry accordingly.  When i go to /media everything is great but the icon on the desktop still has the old name.  

I guess all im asking is Where are the entries for the mounts on the desktop? I'm confused :(

---

### Post by estyles on 2009-03-10
If I remember correctly, the icons on the desktop are generated automatically and point to /media/drivelabel

Where drivelabel is the name of the partition.  If the partition has no label, then I think it goes to /media/disk, /media/disk-1, etc...

I tend to setup fstab to mount in /mnt, and I always turn off desktop icons for mounted drives, because they're just annoying.  If you want a shortcut to your Vista drive, I would just make a link on the desktop.  You can turn off the icons in gconf-editor (just type gconf-editor in the terminal), but I don't recall exactly where the setting is... somewhere under "nautilus", I believe.

---

### Post by prow on 2009-03-10
but why isn't my external HDD in the fstab?

---

### Post by Neo_The_User on 2009-03-10
mount and umount commands might help you out.

Terminal:

```

man mount
man umount

```

---

### Post by estyles on 2009-03-10
> **prow said:**
> but why isn't my external HDD in the fstab?

Most likely?  Because you didn't put it in there.  Nautilus is able to mount drives that are not in your fstab, as long as you have privileges to do that (I think you need to be a member of the "disk" group), which the default user in Ubuntu has.

---

### Post by Neo_The_User on 2009-03-10
> **estyles said:**
> Most likely?  Because you didn't put it in there.  Nautilus is able to mount drives that are not in your fstab, as long as you have privileges to do that (I think you need to be a member of the "disk" group), which the default user in Ubuntu has.

Nautilus doesn't verbose problems when mount or unmounting devices very well hence is why you should use command line. (I probably used the word "hence" wrong but w.e.)

---

### Post by prow on 2009-03-10
> **Neo_The_User said:**
> mount and umount commands might help you out.

Terminal:

```

man mount
man umount

```

thats great, i can mount and unmount whatever i want..but that still has nothing to do with what I'm asking.

i just want the VistaOS and the External HDD to be in /media and on the desktop without nautilus (or whatever is doing it) automatically putting them there.  I would infact like any other drive i plug in be automatically detected.

can i have my cake and eat it too?

---

### Post by Neo_The_User on 2009-03-10
I'm terrible at interpreting things. I'm confused.

---

### Post by prow on 2009-03-10
> **Neo_The_User said:**
> I'm terrible at interpreting things. I'm confused.

no, im just confused.....so, i really dont wanna turn off the automount because i still want flash drives to show up when i mount them but i dont want my vista partition and Xdata drive showing up as "OS" and "LACIE"

they are in fstab as i want them named

i guess im talking about the volume label..thats where i got confused....how can i mask the volume label with something else without changing the volume label?

---

### Post by estyles on 2009-03-11
I don't know how to mask the drive label - I'm sure it's possible, but I suspect it might be more complicated than you would want to deal with.

Is there a problem with changing the drive label?  For the Vista drive, just boot into windows and change the drive name.  For the external drive, it depends on what type of volume it is.  If it's ext3, use e2label in the terminal.  If it's a windows volume, change it in Vista.

---

