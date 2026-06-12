---
title: "Not All Icons Updating"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by ajayre on 2007-11-02
Running a stock Ubuntu 7.10. I don't use compositing.

I downloaded the eXperience icon set from art.gnome.org and stored it in /home/andy/.icons/eXperience. I then went to System -> Preferences -> Appearance and customized the theme to use the icon set.

Nearly all the icons updated to the new set, but some didn't. They are the mounted SMB shared and the home folder. Some ugly fallback defaults are being used. However if I look in the icon set I see:

/home/andy/.icons/eXperience/normal/filesystems/gnome-fs-smb.svg

Why isn't this icon being used? What do I need to do to make Gnome use it?

I see this same problem with several icons sets that I have downloaded. The default Human theme does update the icons when used.

Help! Andy

---

### Post by ajayre on 2007-11-02
Here is the solution:

There is no standard for icon names, so each icon ends up with 10 copies, all with different names to keep  the various applications happy. It seems that many icon sets don't bother to create links for all the icons.

If you go to /usr/share/icons/gnome you can find the icon that is showing up. Note all the names for that icon.

Then go to /home/username/.icons/iconsetname and find the icon you want. Create links (or copy) the icon so it also has all the names you found in the previous step.

Restart Gnome and the icon will be used.

Andy

---

