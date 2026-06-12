---
title: "[SOLVED] Broken USB-HDD mounting"
date: 2008-05-11
forum: Desktop Environments
---

### Post by benpage26 on 2008-05-11
Hi, I just plugged in my USB HDD and right-clicked to get the properties and attempted to change the mount point.  There was an error with the mount point and now i cannot re-mount it to change the properties (it has to be mounted for me to right click and get properties)

What can i do? any help?

PS. I think the error is under the volume tab for mount point i typed /media/mybook/  I think i should have only typed mybook.  Also the referenced folder isn't there yet.

---

### Post by gmaniac on 2008-05-11
Very robust this part indeed!:mad:
As i was experimenting i came across this gem-of-a-problem but with the options part.
To reset it all you have to do is mount your drive from the command line and then after it pops-up on your desktop you can undo your changes.

---

### Post by benpage26 on 2008-05-11
Thanks for the advice, but i just managed to fix it using gconf-editor to change what i would have changed with the properties box without using the properties box.  Also, i wouldn't know how to mount from the command line :(

The key i changed was: /system/storage/volumes/(something about device UID)/mount_point

I changed it to a valid mountpoint such as "mybook" no quotes

---

