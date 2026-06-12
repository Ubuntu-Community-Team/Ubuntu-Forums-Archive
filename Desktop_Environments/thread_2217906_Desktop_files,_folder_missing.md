---
title: "Desktop files, folder missing"
date: 2014-04-18
forum: Desktop Environments
---

### Post by Mark_in_Hollywood on 2014-04-18
This is 12.04 LTS (I checked). Today, I left the computer on and powered down the monitor. Returning hours later, the icons, folder, .pdf-s, etc. are all gone.

On reboot, the above object re-appear briefly then disappear. I have run a backup (using default app: Backup), today before the problem appeared and a 2nd time, after it appeared. I probably have /home securely copies to an external device.

While probably not relevant I was trying to d/l a book from [www.books.google.com](www.books.google.com) today and it would not download, giving a 500 server error on many attempts (10 x) and at least one or two 403 permissions error. Probably not related.

I have been deliberately waiting to upgrade to 14.04 LTS, until the crush died down a little.

I did get 2 updates today, one is "Whoopise", the other youtube-dl.

Output of dmesg is viewable: [http://paste.ubuntu.com/7280083/](http://paste.ubuntu.com/7280083/)

Output of boot.log is viewable: [http://paste.ubuntu.com/7280106/](http://paste.ubuntu.com/7280106/)

Output of auth.log is viewable: [http://paste.ubuntu.com/7280114/](http://paste.ubuntu.com/7280114/)

Also, the mouse, while it can be moved across the desktop, does nothing. It cannot left click and drag (and drop) nor does a right click open a context menu.

---

### Post by Mark_in_Hollywood on 2014-04-20
error:: no video mode activated

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

This flaw (or bug) has caused 2 different problems. It has prevented the desktop (/home/mark/Desktop) from being stable. At boot time (cold or warm) the objects on the /Desktop load, but after a few seconds vanish. The file manager behaves much the same way. When called or invoked the "Folder" icon on my left panel opens for a few seconds, then closes without being commanded to do so. At no time during the on-time for the computer can the file manager (Nautilus?) operate properly. Also, trying to fix this and being mislead by those with Unity or Compiz problem, I have reset my left panel and lost a number of application.

A few days later, I saw, at boot time, one icon which had the look or image of the "i'm still loading" the exact moment went by so swiftly I don't know for certain what it is. But, I decided to delete it. It had a filename extension of .jp2. Ubuntu's various apps cannot read a .jp2. After deleting this file and re-booting, I have the formerly lost desktop objects returned to their places on the /Desktop. For example. *.txt, .jpg, .pdf, user created directories "Trusty Tahr",  desktop configuration file (application/x-desktop), .mp3 and such.

---

