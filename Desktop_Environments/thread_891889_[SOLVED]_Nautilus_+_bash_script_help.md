---
title: "[SOLVED] Nautilus + bash script help"
date: 2008-08-16
forum: Desktop Environments
---

### Post by Nerdriot on 2008-08-16
Hey guys,

I've written a couple of simple scripts for mounting and umounting .iso images in terminal, but I'm trying to simplify them both, make one script, and include it into Nautilus.

This is an example of what I'm trying to accomplish: When you right-click on an .iso, an extra option shows up as "Mount or unmount .iso image". Then, depending on whether or not the image is mounted, it will either mount or umount it. Pretty simple stuff.

My problem is, I can't seem to figure out how to make the script create a directory in /media/ with the name of the selected filename. I saw an example with "$*", but that didn't work for me.

So, any suggestions?

Thanks in advance,

nerdriot

---

### Post by spupy on 2008-08-16
You can get the name of the selected file like this:
```
basename $filename .iso
```
Running this command with **$filename=ubuntu8.10.iso** for example will return **ubuntu8.10**.
Creating the /media folder will look like this (assuming the selected file the first argument to the script - $1):
```
filename=`basename $1 .iso`
gksu mkdir "/media/$filename"
```
I'm not sure about the gksu part because I have no idea how these permissions work out with nautilus.
I hope I understood your question correctly.

---

### Post by Nerdriot on 2008-08-19
Thank you! I'll certainly give this a try asap. :)

---

