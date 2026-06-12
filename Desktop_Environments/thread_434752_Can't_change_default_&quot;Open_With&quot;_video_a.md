---
title: "Can't change default &quot;Open With&quot; video app"
date: 2007-05-06
forum: Desktop Environments
---

### Post by benn333 on 2007-05-06
I'm trying to change the default application that launches video files in Kubuntu, but no matter what I set it to, double-clicking an .avi, .mpg, .wmv, etc. always opens in Kaffeine. I've tired the following steps:

1) Launch Konqueror ("kfmclient openProfile filemanagement" as either normal user or using sudo)
2) Right-click a any type of video file.
3) Select Open With > Other
4) Select any other video app (e.g. xine)
5) Check "Remember application association for this type of file" and click OK.

A window pops up saying it's updating the system configuration and the file plays in the new player. But if I close the app, then double-click the video file again, it opens in Kaffeiine again. Any ideas how to get this change to stick? The same steps work for other file types, such as image files.

(This issue has been present since upgrading from Dapper to Edgy, and is still happening now that I've upgraded to Feisty.)

---

### Post by krussell on 2007-05-06
Hello :-)
Try this, KDE Control Center(kcontrol)>KDE Components>File Associations (look for File Associations, i am not sure whether it is in KDE Components or not, but a little browsing in the Control Center will reveal it). After you find it, look for your desired file type and change the Applications attached to it. Hope this helps you.

---

### Post by benn333 on 2007-05-06
Cheers krussell. You pointed me in the right direction. I pulled Kaffeine out of list in KDE Control Center(kcontrol)>KDE Components>File Associations>Video for all file types. Next time I double clicked an .avi file it opened in Xine, but froze. So I reinstalled Xine and it's respective libraries, and it worked. Thanks again.

---

