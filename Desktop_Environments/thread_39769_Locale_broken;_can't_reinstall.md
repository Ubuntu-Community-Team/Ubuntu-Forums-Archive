---
title: "Locale broken; can't reinstall"
date: 2005-06-06
forum: Desktop Environments
---

### Post by Jonathan2007 on 2005-06-06
Ok just so you guys know I posted this in the Kubuntu/KDE forum but nobody has answered in about 2 days and so I think maybe I can get more help over here. Thanks.

Well here is the whole story. I was downloading using Azureus and I have a pretty small hdd. I ran out of space but I usually don't worry about that. I shutdown my computer and tried to boot back up the next morning . It got stuck on the KDE login screen. I couldn't login to any Window Manger (Gnome, XFCE, Enlightenment, Fluxbox, or KDE) (at this point I had no idea that the hdd being full was a problem as I have had no disk space left before and my computer had booted fine). I could only get to a command prompt. I went on the internet on my laptop and searched to see if this was a bug for KDE 3.4.1 because I had installed that about a day ago. I didn't find anything. So I decided to install GDM to see if it was KDM that was causing the problem. I installed GDM and configured it and reboot. I got the GDM login screen but the same thing happened. BUT it gave me an error saying it couldn't write to the hdd and either the permissions were wrong or I didn't have enough hdd space. I was kind of mad that KDM hadn't told me that because I could have solved the problem a lot quicker if I had known hdd space was the problem. So I got out my Knoppix live cd and booted it up. But I hit another snag. I couldn't delete anything on my hdd. It just gave me an error. I tried to cut and paste stuff to a network drive. I tried to move the stuff to the trash. I tried to delete stuff. Nothing worked. FInally I setup a Samba share and then used my laptop to go in and delete stuff. It worked like a charm. Then I reboot my computer and GDM came up and let me login to KDE. I was very happy. I then wanted to get rid of GDM as I already have KDM customized and didn't want to spend the time customizing with GDM. So I uninstalled GDM using KPackage. At the end of the message it told me to be sure to do a dpkg-reconfigure kdm. It gave me a locale error (yes I did use sudo). So I searched on the internet for locale. It said to install it. So I tried but it said it depended upon glibc-2.3.2.ds1-20ubuntu13. I searched for that and it said it was a virtual package and a part of libc6 2.3.2.ds1-20ubuntu13. Well at some point in time I had upgraded libc6 to version 2.3.2.ds1-21 because something (I forget now) needed that to be installed. Well now I don't know how to get glibc-2.3.2.ds1-20ubuntu13. And I need that to be installed so I can install locales so that I can reconfigure kdm. Well any help would be very very much appreciated. Thanks and sorry for such a long post.

---

### Post by Jonathan2007 on 2005-06-08
Nobody has a solution?

---

### Post by alastair on 2005-06-08
You write far to much dense text and it is hard to read. Too much text - use some paragraphs or bullet points to make it less hard work for us.

Log in as a text user and see what the disk space is :

df

Then, if it IS almost full (/ or /var etc.), make some space. Perhaps try and copy or transfer some large files somwwhere else (USB stick, disk etc.).

Make some space.

remember - you do not need to start GDM/KDM ...

Log in text mode - and you can "startx".

Check the system logs :

/var/log/syslog
/var/log/Xorg.0.log

etc.

The thought of needing this or that C library (glibc,libc) is crazy. There's no need to get a system in such a poor state.

---

### Post by Jonathan2007 on 2005-06-09
Yeah I kind of realized I didn't need that much but I didn't know if some of it might help. 

Anywho basically I updated the libc6 version to 21 and I think it removed locales. And I can't reinstall locales because it depends upon glibc-2.3.2.ds1-20ubuntu13 which is a part of libc6 20 and I have 21. I am sure others have updated their libc6 to 21 and now don't have locales.

I rebooted my computer and KDM still seems to work so I guess it is ok. But I still would like some info about the locales problem.

---

### Post by DancingSun on 2005-08-15
[QUOTE=Jonathan2007]I am sure others have updated their libc6 to 21 and now don't have locales.[/QUOTE]
Well, that's me!

---

### Post by DancingSun on 2005-08-16
I think I fixed the problem!  I just had to reinstall the "locales" package.  After that, the locale error messages will go away, and gparted will start again!

---

