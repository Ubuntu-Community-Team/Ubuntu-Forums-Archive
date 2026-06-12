---
title: "Permissions again"
date: 2005-10-06
forum: Desktop Environments
---

### Post by Rumpty on 2005-10-06
There is, understandably, a fair amount of traffic on the forum about file permissions and the difficulties wrong permissions cause.

There are two annoyances in my case - (1) there is no user access to my flatbed scanner from xsane, and, (2) when trying to import some files from a dig. camera to my home directory, access to the directory is denied.

Sure, I can fix both problems by changing the permissions, but shouldn't both these things work "out of the box"?

I am working on a friend to get her to try Linux - Ubuntu, (she is computer literate, but not a geek), but problems like the above would not help, to put it mildly!

---

### Post by landotter on 2005-10-06
open up the user manager under system--administration and see if you're allowed to use such stuff, and tick the "use scanner devices" box.

If that doesn't work, file a bug report:
[http://bugzilla.ubuntu.com/]("http://bugzilla.ubuntu.com/")

or it won't ever get fixed.

Ubuntu is a community driven effort and such contributions are invaluable.

---

### Post by Rumpty on 2005-10-07
The "use scanner devices" box was already ticked, so I had a look through the bugs relating to scanners, and it seems this problem has been noted, and is fixed. Similarly with importing photos from a digital camera.

I will see if there are any updates for udev, gthumb, and libgphoto2 available from the repositories.

Thanks.

---

### Post by Alexander Kirillov on 2005-10-07
[QUOTE=Rumpty]The "use scanner devices" box was already ticked, so I had a look through the bugs relating to scanners, and it seems this problem has been noted, and is fixed. Similarly with importing photos from a digital camera.

I will see if there are any updates for udev, gthumb, and libgphoto2 available from the repositories.

Thanks.[/QUOTE]
The problem is not with gthumb - so updating gthumb is not going to fix it. I'd rather suggest updating udev, dbus and hal

---

### Post by Rumpty on 2005-10-08
[QUOTE=Alexander Kirillov]The problem is not with gthumb - so updating gthumb is not going to fix it. I'd rather suggest updating udev, dbus and hal[/QUOTE]

I checked udev, and there is no new version of that for hoary. I'll have a look at 
dbus and hal. 

Maybe it is all sorted out in breezy. 

Thanks.

---

