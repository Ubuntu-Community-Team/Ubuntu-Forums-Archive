---
title: "Questions about mounting partition on drive #2"
date: 2009-02-14
forum: General Help
---

### Post by sofasurfer on 2009-02-14
I did not have drive #2 listed in my fstab file. When I want to mount it I just go to 'places>78.6 GB Media' and click on it and then I am prompted for a password and then it is mounted.

Now I try mounting it using the mount command and am told that it can not mount because the drive is not mentioned in fstab. So, since I forgot how to write the fstab entry I used the line out of the mtab file after I mounted the drive using places>78.6. The line looks like this...

/dev/sdb2 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0

It seems to work well.

Now however, the drive is mounted as soon as I boot up. How should I change the line to make the drive NOT mount on bootup? I want to mount it only when needed, with the 'mount' command.

---

### Post by logos34 on 2009-02-14
> **sofasurfer said:**
> How should I change the line to make the drive NOT mount on bootup? I want to mount it only when needed, with the 'mount' command.

'noauto' option

> /dev/sdb2 /media/disk ext3 defaults,noauto 0 0

you might want to use different mountpoint

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by sofasurfer on 2009-02-14
Thanks for you help. It worked fine,
But can you answer me this...
Now that I have configured to enable manual mounting, it is no longer possible to mount using the "places" button. Isn't this actually a link to a manual mount command? Is it possible to still use it?

---

### Post by logos34 on 2009-02-14
I think when you click on the volume in places it tries to mount at the default generic (temporary) mount point '/media/disk,' '/media/disk1', 'media/disk2', etc.  But if there's already a mount point or fstab entry by same name maybe it refuses.  Try another mount point in fstab and rmdir any 'disk' in /media.  Then see if you can mount it in Places

---

