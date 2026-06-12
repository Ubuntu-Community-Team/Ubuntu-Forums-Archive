---
title: "Help pointing to a path on a different drive"
date: 2008-02-21
forum: Desktop Environments
---

### Post by mmacintyre on 2008-02-21
Hi,  I having a tough time here, right now the default path for a program to look for music files is: /var/lib/mythtv/music  now I want to change the default path and  point it to a directory on a different partition /hda5 and I am totally lost on how to do this and figure this out.  I think it should be something like this /dev/hda5/My Music however that is not working and I have tried all the variations with no success.

any help on how to do this would be great.

thanks,
Mike

---

### Post by taurus on 2008-02-21
What program do you use and how did you try to add that new path?  Remember, you probably need to put the new path in quotes since you have a space between My and Music,  On the other hand, you access your /dev/hda5 from the mount point, not the device directly.  So if you mount /dev/hda5 to /media/hda5, then try "/media/hda5/My Music".

---

### Post by mmacintyre on 2008-02-22
thanks I will give that a shot

---

