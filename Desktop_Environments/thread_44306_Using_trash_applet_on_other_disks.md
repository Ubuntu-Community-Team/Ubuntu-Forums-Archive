---
title: "Using trash applet on other disks"
date: 2005-06-25
forum: Desktop Environments
---

### Post by Tomcat_ on 2005-06-25
This is not really a question, but an answer to my own that I couldn't find here, on the Ubuntu wiki, and not even directly using Google. I hope it'll help others.

Today I copied all my important files down from an NTFS drive to my userhome. Then I reformatted the NTFS drive to ext3 and mounted it in /mnt/hdb1.

I'm the only one using this PC, but I still want to keep it open for multi-user access in case I need it. So I created a directory /mnt/hdb1/tomcat with good permissions where I could put my stuff.

Problem: I can't use the trash there. Every time I delete something on /mnt/hdb1/tomcat, I get asked if I want to delete it immediately because the trash is not usable.

Searching around for about an hour on Google turned up this: [http://lists.freedesktop.org/archives/xdg/2004-August/004539.html](http://lists.freedesktop.org/archives/xdg/2004-August/004539.html)

Apparently you need to create a directory $MOUNTPOINT/.Trash-$USER. Gnome will do that automatically, but of course my Gnome didn't have the permissions to create the directory /mnt/hdb1/.Trash-tomcat.

Doing that myself, changing ownership (tomcat.tomcat) and permissions (700), everything worked again. I can now delete files in /mnt/hdb1/tomcat using the trash.

I also posted a detailed explanation and HowTo on the Ubuntu wiki: [https://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2005-06-25.4735097402/faq_view](https://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2005-06-25.4735097402/faq_view)

---

