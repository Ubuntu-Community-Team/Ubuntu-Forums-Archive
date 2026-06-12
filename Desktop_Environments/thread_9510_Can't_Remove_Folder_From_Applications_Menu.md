---
title: "Can't Remove Folder From Applications Menu"
date: 2004-12-29
forum: Desktop Environments
---

### Post by vaughty on 2004-12-29
Hi,

I installed CrossOverOffice to see how well it ran Flash MX (the only reason I still dual boot) and it is pretty buggy.

Anyway I uninstalled it but now I'm stuck with an 'empty' CrossOver folder in the Applications menu panel.

I've tried using Nautilus to remove it, in both **applications** and **applications-all-users**, and it doesn't appear there but nothing will get rid of it from the Applications menu.

I have also tried un-installing and then re-installing gnome but with no avail.

Is there anyway to go back to the default installation of gnome (I'm not bothered about losing my 'look' I just want to get rid of this folder)?

Thanks,
vaughty

---

### Post by hardcandy on 2004-12-29
If you are talking about the drop down menu, go to the crossover folder and right click on it. It should bring up a menu to delete it, add to it, etc.

---

### Post by rbran100 on 2004-12-29
have you tried looking in /etc/gnome-vfs-2.0/vfolders to see if it is in one of the folders there?

---

### Post by vaughty on 2004-12-29
@hardcandy - there was no option to right-click on any of the folders to delete it, it was only possible on the sub-menus/folders.

@rbran100 - I had a look in /etc/gnome-vfs-2.0/vfolders and found some references to CrossOverOffice so I deleted them. This proved to be a bit of a mistake because having only one folder that I didn't want I now have nearly all of my folders missing.

[IMG]http://www.2-mail.co.uk/apps.png[/IMG] 


vaughty

---

### Post by rbran100 on 2004-12-29
Yikes that is no good, not sure what you did; but i suggest putting it back.  I thought that everything was either pulled from that dir or from the .gnome directory in your home.....

You can type what is before the .vfolder-info in the Location menu of natulus with a colon at the end and see the contents of each menu :-x

Sorry that is the only way i know to remove it, i don't know where else it could be pulled from.

You have checked the /home/username/.gnome directory right?

---

