---
title: "Thunar not recognizing new internal HDs"
date: 2009-04-05
forum: Desktop Environments
---

### Post by stans on 2009-04-05
I've just added two internal drives but Thunar doesn't display them in the left viewing pane. The Open Office apps all see them, and other apps see them. The disk icons are displayed on the desktop and can be opened. 

The new drives are sdb1 and sdc1 in the fstab shown below:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=e35501d9-476a-42ac-aa90-e6cf855dda5f /media/diskb    ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=dde6aa0b-a8aa-4c73-ba42-f0b6cb45b934 /media/diskc     ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8a462438-77e4-4138-86f1-3810c73931f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

-----------------------------------------------------------------------

Any ideas ?  Thank You...

---

### Post by adamlau on 2009-04-05
thunar-volman-plugin installed?

---

### Post by stans on 2009-04-05
I just did that, and see no difference. Perhaps I need to reboot ?

Thank you for the reply and suggestion...

(You are a neighbor btw...)

---

### Post by stans on 2009-04-06
OK then - installed Krusader and it does see the new drives... but the problem is unless I invoke Krusader via sudo I get a permission problem. 

Cannot write to the new drives otherwise.

How can I get around this problem ? When I assigned write permission to the new drives it was as ROOT.

---

### Post by vanadium on 2009-04-06
You don't have a problem. Probably, thunar is not designed for displaying a "drive icon" (a Windows thing) for drives mounted under /media (I do not know thunar myself).

Probably thunar has, like nautilus, a way to create bookmarks for easy access to a location.

Alternatively, you can create symbolic links in your home directory for one click access to the drives from within your home directory.

---

### Post by stans on 2009-04-06
That would work - but how does one accomplish it ? 

Cannot 'man symbolic link'.

---

### Post by thomasboleyn on 2009-04-06
I am experiencing a similar problem - I have created a fat32 partition on my 300gb drive to share music and movies between vista and xubuntu (both on their own partitions). Thunar does not seem to be able to 'see' this new partition, though nautilus does. I installed pcman file manager instead which is able to see it. Not an ideal solution but I'm very impatient!

---

### Post by vanadium on 2009-04-06
Command line tool is "ln" with the -s option.

In nautilus, you can create one dragging with Ctrl+Shift pressed down or using the right click menu.

Thunar probably also has a facility. If not, then command line, e.g.

```

ln -s /media/mydrive ~/mylink

```

---

### Post by stans on 2009-04-06
I've done that command substituting disk1 and disk2 for 'mydrive'. 

I don't see them in Thunar...

Also - when I invoke Krusader I get a permission problem when trying to write to the new drives. How can I resolve that ?

---

### Post by vanadium on 2009-04-07
> substituting disk1 and disk2
Where did you get that? This is not what is mentionned in the /etc/fstab you posted. That one makes reference to a /media/diskb and /media/diskc.

If you try a command and get problems, it is useful to post both command and output back here. Then we can know what eventually went wrong. Otherwise, it is guessing.

---

### Post by stans on 2009-04-07
My mistake. I had the names wrong. Still cannot see them with Thunar. How do I access them with Thunar ?

I can see the drives with Krusader, but cannot write to them unless it is using 'sudo'. Not sure how to change the permissions though. 

How do I change the permissions so that any application can write to these new internal drives ?

Thank you for your assistance...

---

### Post by vanadium on 2009-04-07
This is another problem, one of linux permissions. You need to change permissions or ownership of the directories (eventually the mount point of a drive) where you want a specific user to have specific rights. You might want to raise this issue in the "Absolute Beginners" section of this forum (or probably previous posts might help you).

---

### Post by stans on 2009-04-07
Thanks again. 'Previous posts' are my first stop - usually for several hours sifting thru the questions and answers. 

Sorry to have asked an inappropriate question for this particular part of the forum.

---

### Post by vanadium on 2009-04-07
Don't worry too much ;) It is good practice to use one thread for one problem. That keeps it more useful for other users looking for solutions.

---

### Post by stans on 2009-04-07
Worry ? No - I was more concerned that I was getting scolded.

I've benefited many times from finding multiple subjects in a single posting.

---

