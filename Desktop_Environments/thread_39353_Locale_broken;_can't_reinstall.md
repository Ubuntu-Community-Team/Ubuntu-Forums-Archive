---
title: "Locale broken; can't reinstall"
date: 2005-06-04
forum: Desktop Environments
---

### Post by Jonathan2007 on 2005-06-04
Ok. Here I go again. I know this isn't really KDE/Kubuntu related but hopefully you guys can help me out.

Ok. Well here is the whole story. I was downloading using Azureus and I have a pretty small hdd. I ran out of space but I usually don't worry about that. I shutdown my computer and tried to boot back up the next morning . It got stuck on the KDE login screen. I couldn't login to any Window Manger (Gnome, XFCE, Enlightenment, Fluxbox, or KDE) (at this point I had no idea that the hdd being full was a problem as I have had no disk space left before and my computer had booted fine). I could only get to a command prompt. I went on the internet on my laptop and searched to see if this was a bug for KDE 3.4.1 because I had installed that about a day ago. I didn't find anything. So I decided to install GDM to see if it was KDM that was causing the problem. I installed GDM and configured it and reboot. I got the GDM login screen but the same thing happened. BUT it gave me an error saying it couldn't write to the hdd and either the permissions were wrong or I didn't have enough hdd space. I was kind of mad that KDM hadn't told me that because I could have solved the problem a lot quicker if I had known hdd space was the problem. So I got out my Knoppix live cd and booted it up. But I hit another snag. I couldn't delete anything on my hdd. It just gave me an error. I tried to cut and paste stuff to a network drive. I tried to move the stuff to the trash. I tried to delete stuff. Nothing worked. FInally I setup a Samba share and then used my laptop to go in and delete stuff. It worked like a charm. Then I reboot my computer and GDM came up and let me login to KDE. I was very happy. I then wanted to get rid of GDM as I already have KDM customized and didn't want to spend the time customizing with GDM. So I uninstalled GDM using KPackage. At the end of the message it told me to be sure to do a dpkg-reconfigure kdm. It gave me a locale error (yes I did use sudo). So I searched on the internet for locale. It said to install it. So I tried but it said it depended upon glibc-2.3.2.ds1-20ubuntu13. I searched for that and it said it was a virtual package and a part of libc6 2.3.2.ds1-20ubuntu13. Well at some point in time I had upgraded libc6 to version 2.3.2.ds1-21 because something (I forget now) needed that to be installed. Well now I don't know how to get glibc-2.3.2.ds1-20ubuntu13. And I need that to be installed so I can install locales so that I can reconfigure kdm. Well any help would be very very much appreciated. Thanks and sorry for such a long post.

---

### Post by Jonathan2007 on 2005-06-05
Sorry to bump this again but does anyone have a solution to this? Surely others have updated their libc6 and no have a problem with the locales package?  :?  I want to get this solved so my computer doesn't have to run when I am not using it. Thanks.

---

