---
title: "Mounted Drives on Desktop"
date: 2005-08-01
forum: Desktop Environments
---

### Post by dahli.llama on 2005-08-01
How do I keep Ubuntu from placing a link to my mounted drives on my desktop?

I currently have 2 CD-ROM drives and a Windows drive that show up on my desktop.  I don't like it and don't want them there.  I can't seem to find a way to get rid of the icons other than to unmount the drives and I don't want to do that.  Could anyone help?

Thanks.

---

### Post by Omnios on 2005-08-01
Open menu applications/system tools/configuration editor.

 In editor navigate /apps/nautilus/desktop/  uncheck volumes_visable.

---

### Post by dahli.llama on 2005-08-02
Thanks

---

### Post by snafoo on 2005-08-03
Same issue, contrary problem.

I do have the /apps/nautilus/desktop/volumes_visable option checked, but my mounted drives won't show up on the desktop. But they should...

Any ideas?

---

### Post by Omnios on 2005-08-03
I take it your talking about a hard drive.

 I found that counting on how you mount your hard drive it may or may not show pertaining to weather its root/ user but I think the inportant part is having groups as group. 

 This a link on a topic pertaining to mounting hd's

[http://ubuntuforums.org/showthread.php?t=49830](http://ubuntuforums.org/showthread.php?t=49830)

This is what I currently use.

```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0 
``` 
change /dev/hda? to your drive id

 Hopefully this works for you, might not work for an external though.

---

### Post by snafoo on 2005-08-03
I changed the entry in fstab for that particular drive partition as of your suggestions. But no luck. My external USB hard drive schows up on the desktop when I plug it in, so basically it's working.

> ...but I think the inportant part is having groups as group.

What do you mean with that?

---

