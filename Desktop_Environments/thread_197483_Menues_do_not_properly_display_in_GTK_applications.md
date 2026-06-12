---
title: "Menues do not properly display in GTK applications"
date: 2006-06-15
forum: Desktop Environments
---

### Post by AtticusFinch on 2006-06-15
In GTK applications the menus do not display correctly. In the place where a letter should be, I see four small numbers instead. The screenshot shows my desktop with Gimp and Firefox open. [IMG]http://ubuntuforums.org/gallery/files/1/2/4/8/9/4/snapshot1.png[/IMG] Interestingly the menus in Firefox display but the save box still has the funny fonts. Whats wrong with my Kunbuntu installation?

Thank you

---

### Post by asimon on 2006-06-16
Try starting 'System Settings' and have a look at Appearance->GTK styles and fonts->GTK fonts. Maybe you have some strange font defined there?

---

### Post by Snover on 2006-06-17
I had this same problem. It occured when I tried using fonts I copied over from a Windows installation. The reason for *my* problem was that the default mount options for an NTFS partition in 6.06 left some really wacky file permissions on the copied files (550). So, if you copied some files from another OS installation and they appeared properly when running fc-cache but then don't work in your software, check the permissions. Otherwise, if you've got an missing/inaccessible font written in ~/.gtkrc-2.0, you will also experience this issue.

---

### Post by AtticusFinch on 2006-06-27
Thank you Snover,

that's exactly what happende. I had copied the Tahoma font from my windows installation. After fixing the permissions, everything worked out beautifully.

---

