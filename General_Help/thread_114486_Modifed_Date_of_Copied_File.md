---
title: "Modifed Date of Copied File"
date: 2006-01-08
forum: General Help
---

### Post by SteveF on 2006-01-08
When I copy files to a mounted vfat partition, I lose the last modified date (it shows the current date).  This doesn;t happen when I copy to an EXT3 partition.

I want to keep the original modified date.  Is this a setting I can change in my fstab or is this a limitation of using the vfat partition?

Thanks,

Steve

---

### Post by Susana on 2006-01-08
[QUOTE=SteveF]
I want to keep the original modified date. [/QUOTE]


```

$ man cp | grep timestamps
Reformatting cp(1), please wait...
       -p     same as --preserve=mode,ownership,timestamps
              ship,timestamps), if possible additional attributes: links, all

```

try using cp with -p option to see if it works.

---

### Post by SteveF on 2006-01-10
Thanks for the suggestion.  I tried cp -p and I got the message [COLOR="Red"]Operation not permitted[/COLOR].  So I tried [COLOR="Red"]sudo cp -p[/COLOR] and that worked (with messages about not being able to preserve ownership).

Though that worked, I prefer not having to use sudo for copying.  My fstab for the mount is:
/dev/hdb1       /staging        vfat    rw,exec,auto,nouser,async,gid=1001,umask=0002   0       0

Is maybe my umask incorrect?

Steve

---

### Post by Susana on 2006-01-11
[QUOTE=SteveF]Thanks for the suggestion.  I tried cp -p and I got the message [COLOR="Red"]Operation not permitted[/COLOR].  So I tried [COLOR="Red"]sudo cp -p[/COLOR] and that worked (with messages about not being able to preserve ownership).

Though that worked, I prefer not having to use sudo for copying.  My fstab for the mount is:
/dev/hdb1       /staging        vfat    rw,exec,auto,nouser,async,gid=1001,umask=0002   0       0

Is maybe my umask incorrect?

Steve[/QUOTE]

Hi SteveF,

I tried your fstab line and it seems that in order to be able to preserve the timestamps assingning the floppy to your group (with permitions) is not enough. It lets you copy normally but not preserve atributes. So to be owner you either change "nouser" to "user" (and all users will be able to mount the floppy) or specify uid=youruid for ownership (and keep mounting and umounting only to root as you have now).

---

### Post by SteveF on 2006-01-11
[QUOTE=Susana]Hi SteveF,

I tried your fstab line and it seems that in order to be able to preserve the timestamps assingning the floppy to your group (with permitions) is not enough. It lets you copy normally but not preserve atributes. So to be owner you either change "nouser" to "user" (and all users will be able to mount the floppy) or specify uid=youruid for ownership (and keep mounting and umounting only to root as you have now).[/QUOTE]

Thanks for looking into this.  I guess I'll rely on uid for now.  It's a hard drive I use to transfer files between Linux and Windows and I'll probably be the only one using it for now.

Steve

---

