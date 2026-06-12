---
title: "How do you delete mount points??"
date: 2009-02-25
forum: General Help
---

### Post by johnson8707 on 2009-02-25
So I have some mount points I created that I am no longer using and want to get rid of. How do you delete them?


THANKS!!!

---

### Post by x22 on 2009-02-25
well, a mount point is a directory, say /mount_point
then in a root terminal "rmdir /mount_point"

---

### Post by heindsight on 2009-02-25
First make sure it's unmounted:
```
sudo umount mountpoint
```

Then edit /etc/fstab and remove the mountpoint from there.

finally delete the mountpoint from your filesystem:
```
sudo rmdir mountpoint
```

---

### Post by johnson8707 on 2009-02-25
Alright, I got all of them deleted except one.

The mount point is called "mb:\\chs-ms1\schools" and is located in the root folder. There is nothing within this folder. It is JUST a folder named "mb:\\chs-ms1\schools"

I enter:
> sudo rmdir /mb:\\chs-ms1\schools

When I do this it says no such directory is found. It seems to be searching for a schools folder within this folder instead of seeing that as the entire name of the folder.

Any suggestions?

---

### Post by TwiceOver on 2009-02-25
Whenever I have problems removing non-standard directory names like that I just use the tab key.

Try rmdir mb then hit the tab key to see if it fills in the remainder for you.

---

### Post by johnson8707 on 2009-02-25
That worked!

THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU!!!!!!!

---

