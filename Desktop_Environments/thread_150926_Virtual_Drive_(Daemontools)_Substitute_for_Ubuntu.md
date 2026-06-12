---
title: "Virtual Drive (Daemontools) Substitute for Ubuntu?"
date: 2006-03-26
forum: Desktop Environments
---

### Post by bluemike807 on 2006-03-26
Can anyone point me in the direction of a program which provides the same functionality - creating virtual drives from .iso or other disc images - for Ubuntu?

Thanks

---

### Post by claydoh on 2006-03-27
you don't need a separate program.

You can run the following command to mount an iso

sudo mount -o loop -t iso9660 /full/path/to/myfile.iso /home/<username>/Desktop/My_Folder

You will need to make the folder first. 
Here is a [right-click servicemenu ]("http://www.kde-apps.org/content/show.php?content=11577")that makes this easier, but I have not tried this in Ubuntu.
__[URL="http://www.kde-apps.org/content/show.php?content=11577"]
[/URL]

---

