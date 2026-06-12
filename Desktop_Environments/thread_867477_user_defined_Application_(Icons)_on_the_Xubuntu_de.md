---
title: "user defined Application (Icons) on the Xubuntu desktop"
date: 2008-07-22
forum: Desktop Environments
---

### Post by boondocks on 2008-07-22
How do I put icons for these applications on the Xubuntu desktop?

/usr/bin/firefox
/home/me/applications/custom_App_1
/usr/bin/pidgin
/home/myFriend/shared_folder/other_App_2
/usr/bin/gnome-terminal

---

### Post by bujutsukai on 2008-07-23
In ubuntu, you can right click the desktop, select "Create Launcher," and fill in the appropriate fields (there's a 'browse to' option) for the application you wish to add.  The icon will pull from the application.

Is it different in xubuntu?  They're both Gnome desktop, right?

Maybe this helps?

---

### Post by madm0nk on 2008-07-23
This might help.

[http://www.linuxquestions.org/questions/slackware-14/xfce-desktop-icons-404020/](http://www.linuxquestions.org/questions/slackware-14/xfce-desktop-icons-404020/)

It looks like iDesk might be your best bet.

---

### Post by boondocks on 2008-07-23
The desktop is Xfce.
When I right-click on the desktop, I do not see any "Create Launcher" option.

---

### Post by madm0nk on 2008-07-23
> **boondocks said:**
> The desktop is Xfce.
When I right-click on the desktop, I do not see any "Create Launcher" option.

Read the reply above. Or just open a terminal and type sudo apt-get install idesk =P

---

### Post by denham2010 on 2008-07-24
It's a little different in Xfce.

Right click on an existing desktop icon (trash for example) and select Desktop > Create Launcher.

Alternatively, if a .desktop file for the program already exists (firefox for example), open thunar and navigate to /usr/share/applications (local .desktop files are in /home/username/.local/applications) find the launcher you want and just drag it to the desktop. This will create a copy of the launcher on the desktop.


Cheers.

---

### Post by madm0nk on 2008-07-24
Ok I just installed xfce on my Ubuntu and it figures they setup and configure that for you

---

