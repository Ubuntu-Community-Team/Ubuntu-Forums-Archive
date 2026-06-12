---
title: "Can't access home folder through file browser"
date: 2011-08-15
forum: Desktop Environments
---

### Post by am1m on 2011-08-15
Hi All,

I can't access any of the sub-folders or files in my home folder on Ubuntu. 

I've checked the folder associations, that doesn't seem to be the issue. I've also opened the mimeapps.list file and the inode/directory association seems fine - inode/directory=nautilus-folder-handler.desktop;

I'm running Intrepid (8.10) (please don't ask me to upgrade! :)) and the issue started after using Qtpfsgui 1.9.3 a couple of time to create HDR images. I guess Qtpfsgui broke an association somewhere, but where? I can access other folders, on Computer and Filesystem, but not on my home folder.

Any help will be very appreciated. Thanks!

Amit

---

### Post by am1m on 2011-08-15
Solved! Listed the files through Terminal, there were 3 files that I guess Qtpfsgui created directly under my home folder. Deleted them and now I can access all the files and sub-folders through file browser. Weird!

---

