---
title: "help on how to fix GDM needed"
date: 2009-02-17
forum: General Help
---

### Post by tropdoug on 2009-02-17
I broke the GUI log in, when I switched sessions from KDE back to Gnome a couple of weeks ago, then decided to stick with gnome, I went on the war path to clean all the Kde apps off and only use Gnome. Hmm all was going well until I decided to remove kwin, and suddenly I cannot log in on boot with a graphical interface. What happens is that the system says there is no resume image available and sits me at a text line desktop prompt. I put in my user name and password and get into my system but then have to do a "sudo gdm" to start the desktop xserver (I think thats what it is) After that it's fine. 

I have tried resetting gdm as the default but every time I log out even if I specificaly pick the gnome session then log in the next time its back to the text stuff. 

How do I reinstall or fix what is broken?

---

### Post by geirha on 2009-02-17
Try running ```
sudo dpkg-reconfigure gdm
```

---

### Post by tropdoug on 2009-02-17
Did that - no change

---

### Post by kimberlite on 2009-02-17
You may try:
```

sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Darkshade on 2009-02-17
Did you have KDM set as default login before?
If yes change the contents of /etc/X11/default-display-manager from ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
```

Good luck!

---

### Post by tropdoug on 2009-02-19
Thought you had got it, darkshade, but when I opened /etc/X11/default-display-manager I found it was already set to /usr/sbin/gdm so offI went to try Kimberlite fix -- and downlaoding stuff right now. 

a Question - I don't use ekiga I have a permanent Hard VOIP phone, and my desktop machine does not have bluetooth capability (least ways I don't think it does) and I use Google apps for all my communication and calender needs, so can I uninstall those apps that deal with these areas. without harming the desktop system, or do I have to leave them sitting taking up space and probably resources, simply because they formed part of a package? 

maybe that was the issue. Hmmm OK its installed so I will re boot and let you all know the result

[COLOR=Blue]EDIT  Well that wasn't it, however I studied the boot messages and saw that the system is looking for kinit -- which would be the KDE init file I believe. SO I would like to be able to find the log of the messages during boot so that I could post the relative point, cos obviously there are broken links to the gnome files needed to get me through to the login window. Anyone know where that log is and what it is called. (I have looked in /Var/log/ but couldn't find it.[/COLOR]

---

### Post by tropdoug on 2009-02-20
Bump

---

### Post by kimberlite on 2009-02-21
Dear tropdoug,
(1.) You can check ~/.xsession-errors and see if there are any critical error.
(2.) Another option is to move .gnome* .gconf* .metacity* configuration files, and let Gnome to re-generate them. 
(3.) You may get some hints from this post: 
[http://tnerd.com/2008/11/12/how-to-uninstall-or-remove-kde-and-restore-gnome-desktop-manager-in-ubuntu/](http://tnerd.com/2008/11/12/how-to-uninstall-or-remove-kde-and-restore-gnome-desktop-manager-in-ubuntu/)
Cheers.

---

### Post by Yashiro on 2009-02-21
The 'no resume image found' and 'kinit' messages are normal on all systems.

---

