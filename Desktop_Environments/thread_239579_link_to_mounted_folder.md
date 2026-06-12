---
title: "link to mounted folder"
date: 2006-08-19
forum: Desktop Environments
---

### Post by npodges on 2006-08-19
When I'm viewing files on a mounted partition, it doesn't let me make a link. I'd like to make a link to my music folder, but the "make link" option is greyed out. Is it possible to link to such files/folders?

---

### Post by aysiu on 2006-08-19
First, make sure your partition is mounted with the correct permissions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

Let's say your partition is mounted to /media/data and you want it linked to your desktop. Paste this command in the terminal: ```
ln -s /media/data ~/Desktop/data
``` Alternatively, you can middle-click-drag the folder to your desktop and select **link here**.

---

