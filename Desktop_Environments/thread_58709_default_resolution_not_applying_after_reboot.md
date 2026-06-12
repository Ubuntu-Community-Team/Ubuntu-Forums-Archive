---
title: "default resolution not applying after reboot"
date: 2005-08-21
forum: Desktop Environments
---

### Post by 5-HT on 2005-08-21
Hi, just installed ubuntu today and am having a problem where my pc boots up with a screen resolution of 1600x1200.

I'd like to use 1280x1024, and can go into system/preferences/screen resolution and change it to 1280x1024 with no problems.
However, when I log out or shutdown, the next time loggin on my resolution is right back to 1600x1200.

(I did select the option to "Make default for this computer").

After a search on the forum, this post ([http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5](http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5)) seemed to describe my problem. I followed it but I'm still experiencing the same issue.

Anyone have any ideas?

thanks for any help

---

### Post by floppy on 2005-08-21
I had this issue also. What I did was edit my xorg.conf file to eliminate the higher resolution. To do so, use these commands in a terminal:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo gedit /etc/X11/xorg.conf

Note: the first command makes a backup copy of the file in case of problems.

find the section titled "Screen" and remove the 1600x1200 items.
save the file, then restart gnome (reboot if you don't know how :), that's what I do)

Hope this helps.

---

### Post by 5-HT on 2005-08-21
Thanks for the help!

Yup that solved the problem nicely. 

It would be nice to be able to still enable the higher resolution in xorg.config but just not default to it...though looks like for some reason if ubuntu see it there, it doesn't like not using it.

I guess I can always just edit the file again (or restore the backup) if I ever want to use a higher resolution in the future.

Thanks again.

---

