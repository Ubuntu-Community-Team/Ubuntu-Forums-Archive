---
title: "ati drivers issue..."
date: 2007-01-19
forum: Desktop Environments
---

### Post by xtlosx on 2007-01-19
Guys Question,

Brand new install, Ubuntu 6.10, ati drivers 8.32, from the ati site for a mobility radeon x1300.....  i followed this guide....
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

when i reboot the computer.... the login screen shows up, and the resolution is noticeable... looks better, i enter my username, password.... and i hear the login sound, but the password field is grayed out and the screen NEVER moves... this happened last night... what is going on here???  What do i do????

---

### Post by puneit on 2007-01-19
Latest drivers of ATI are not very stable for all kinds of cards. You can attempt to downgrade the driver to 8.30.3 or 8.29.6
And for accessing the system again, you can copy the x.org.backup file that you created in /etc/X11 to xorg.conf
to enter the command line press ctrl+alt+f1 
```
cd /etc/X11
ls

```
this will list the  xorg.conf.* files you have
copy the file xorg.conf.original or backup whatever is the name to xorg.conf
eg. In my computer the backup file is called xorg.conf.original-0
so the copy command will be 

```
sudo cp xorg.conf.original-0 xorg.conf
```

after this retsart the system. You should be able to get to the desktop and work
For restarting issue the following command ```
sudo shutdown -r now
```

---

