---
title: "Missing desktop-integration folder in OpenOffice 3.2 development build"
date: 2009-04-24
forum: General Help
---

### Post by Jags_FL on 2009-04-24
I'm trying to install OpenOffice development build ( x86 deb from here : [http://download.openoffice.org/next/other.html#dev2](http://download.openoffice.org/next/other.html#dev2) ) per this tutorial :
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

But it fails to create shortcuts in applications menu as its missing desktop-integration subfolder within DEBS folder... 

Is there any workaround to create shortcuts without 'openoffice.org3.0-debian-menus_3.x-xxxx_all.deb' package ? Many thanks.

---

### Post by Jags_FL on 2009-04-24
anyone who has installed OpenOffice dev build/RC ?? Thanks.

---

### Post by Psychoscorpic on 2009-05-10
If it's any consolation, I just lost my menu entries after upgrading to 3.1 official build.
Have you found a solution yet?

---

### Post by Jags_FL on 2009-05-10
> **Psychoscorpic said:**
> If it's any consolation, I just lost my menu entries after upgrading to 3.1 official build.
Have you found a solution yet?

No. And its little unusual but true that the thread received no replies !

---

### Post by Giant Speck on 2009-05-31
I'd like to bump this as I can't figure it out either.

---

### Post by Psychoscorpic on 2009-06-01
Hi Giant Speck

I discovered mine hadn't actually installed properly after all. Had some network problems with the download that I left unattended overnight, it seems. Synaptic showed the process as complete, but it wasn't really. I uninstalled (not complete removal) and after a reboot (may not be necessary) re-installed it, and lo - it downloaded a whole lot more, meaning that the packages on my system were not complete.
All was happy after that.

(As an aside, the whole thing was auto-reinstalled again a few days later when the OO3.1 repository had the file names corrected. As far as I know, there were no actual data changes, but Synaptic saw it as a fresher version.)

---

### Post by Boondock5 on 2010-02-24
Not sure if this is the same problem.
When I upgraded to 9.10, all the text went away in Open Office's menu/toolbar, There are empty spaces and even drop down menus, but no text in the boxes or menus. I can't even save a document, because I can't tell which button is save.  I have a screen shot but can't seem to get it posted here for some reason.
If this is the wrong place to post this, I'm sorry, I was havining trouble finding a place to post it.
I'm new to the linux/Ubuntu world. Please be patient.

Dell 640, Ubuntu 9.10, Open Office 3.2

Thanks in advance. B

---

### Post by Hagar Delest on 2010-02-25
No this is not the same problem!

For the initial problem about desktop-integration, its lack of is by design because developer builds are not to be used for production. So to avoid problems with the developer version taking precedence on the stable version (they can both run in parallel), the menus are not updated. To use the unstable version, you've to create the entries yourself.

For the empty menus in OOo, see that one, several fixes (read until the end): [[Solved] No text in OpenOffice menus](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183).

---

