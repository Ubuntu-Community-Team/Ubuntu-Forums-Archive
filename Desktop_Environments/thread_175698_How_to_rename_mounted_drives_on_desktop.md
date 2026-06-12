---
title: "How to rename mounted drives on desktop"
date: 2006-05-13
forum: Desktop Environments
---

### Post by lee_connell on 2006-05-13
How do you rename the mounted drives on the desktop?  I have some auto-mounted drives that appear on my desktop and I want to rename them to something useful.

---

### Post by aysiu on 2006-05-13
Let's say you have a drive mounted at /other_drive

You would paste this command into the terminal: ```
sudo ln -s /other_drive ~/Desktop/name_i_want_to_appear_for_other_drive
```

---

### Post by lee_connell on 2006-05-13
No I don't want to create a link to it.

I want to rename the existing icon on my desktop.  These are the actualy disk icons which are created on boot.

How do I rename the existing ones?

---

### Post by Ramses de Norre on 2006-05-13
Set the link instead of the icons, that's the easiest fix.
Turn them off with gconf-editor /apps/nautilus/desktop/volumes_visible.

---

### Post by lee_connell on 2006-05-13
thanks for the tip.

however the volumes won't show up in the nautilus sidebar or open dialogs.

I would like to know how to change the existing volume names.

thanks.

---

### Post by Omnios on 2006-05-13
Not shure if this will work on your set up counting how they are automounted. Anyways I have a Vfat 32 drive that I mounted by changing the the name of the directory it was mounted to to Documents. Or jsut create a directory in /media called Docuements. Now you will have to go int fstab. 
In terminal  create a backup file sudo "cp /etc/fstab /etc/fstab-backup"
```

sudo gedit /etc/fwstab
```

 This a line in mine.
```

/dev/hda2       /media/Documents    vfat    rw,users,gid=users,umask=000,       0       0
```
Now /dev/hda2  is the partition name so you will need to see what partition you want. Now the next part is what you want to change /media/Documents, this is the directory your partition mounts to so if you want to change the name of the directory or make a new directory this should be changed to that name. 

 Now this is not garenteed to work buy on my system it when't from like 50gig drive to Documents. 
Cheers and good luck.

---

