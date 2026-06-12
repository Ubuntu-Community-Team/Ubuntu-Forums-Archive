---
title: "Cannot write all the mounted partition."
date: 2006-08-16
forum: Desktop Environments
---

### Post by hecato on 2006-08-16
Hi there.

my fstab

Contain this line (I have added it, because I dont define it like a mount point when installing).

```

/dev/hda3       /home/hecato/Desktop/hda3_reiserfs    reiserfs    defaults     0       2

```


That partition hold the backup of my anterior system (I have copied old hda6, hda11 and others).


I have created with my normal user 2 folder in my Desktop
```

hda3_reiserfs
hda3_reiserfs

```


But when is mounted in any of them, it get no write permission at first level, some of the internal folders:hda6, hda11 let me create and remove. But the other folders are only modificable by the root.


Here is a screenshot that display the 2 folder (1 of them have actually mounted the resiserfs partition), and the command line that show how is mounted...

[IMG]http://img227.imageshack.us/img227/4551/hda3ch7.jpg[/IMG]


You know what is happening???





By the way I have done "sudo" and "su " and chown hecato:hecato when mounted the partition, but the owner in propierties still root)
, the only way to get back mi folder for my user that is hecato:hecato and not root:root is unmounting the hda3... (like the second folder that dosent have a red padlock.


Another suguestion??

---

### Post by Jussi Kukkonen on 2006-08-16
mount point is owned by the mounting user. Try adding option "user" to your mount options, then you can mount it without becoming super-user. That should help.

---

### Post by RAOF on 2006-08-16
You should **sudo chown -R hecato:hecato /home/hecato/Desktop/hda3_reiserfs**.  The -R switch says "recursive" - that is, do it to the folder, and everything in it, and all the folders within it, and...

---

### Post by hecato on 2006-08-16
The solution was the combination of the 2 solutions...

add defaults,**user **and after unmount and mount again, and for the internal directories taht wheren't writeable in that moment the show recursive worked.



By the way, I always tought that user where in defaults??? 

And a question I will solve in next reebot (like in 8 or more hours\\:D/), should I always to unmount it (if mounted at boot.. start) and do

```

mount /dev/hda3

```

In a console of my user, or the next time I reebot it will get OK for me?

(anyway if you dont whant to answer, next reboot will show it).

---

### Post by hecato on 2006-08-16
Hi there, Im thinking why it dosent show the partition (now that all work OK) in the "places" or in the Save/Open dialog...

[IMG]http://img49.imageshack.us/img49/3866/agregarpathkl2.jpg[/IMG]

I will like that my hda3 is listed in the places at top panel, for save/open dialog \\:D/

---

