---
title: "How to change the icons of Nautilus (manually)?"
date: 2006-04-13
forum: Desktop Environments
---

### Post by sha_man on 2006-04-13
Hello,
I want to change the icons of Nautilus, but manually (because the iconset has none for it). In Konqueror (if only it was *just* a filemanager, I wouldn't hesitate to use it), this is easy to be done but in Nautilus??

---

### Post by Ubuntuud on 2006-04-13
Do you mean icon by icon, or do you wish to mod your current set group by group

---

### Post by sha_man on 2006-04-13
icon by icon

---

### Post by Irony on 2006-04-13
Look in the mimetypes folders in;

[PHP]/usr/share/icons/[/PHP]

Just replace whatever .png icon you want with the icon of your choice - keep a copy of the one you replace until you know the replacement works.

For example 

[PHP]/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-text-plain.png[/PHP]

specifies the gedit icon. Note there are different themes, thus there are several mimetype folders - also you can add themes; [http://www.gnome-look.org/index.php?xcontentmode=120](http://www.gnome-look.org/index.php?xcontentmode=120)

Thus I am using a OSX theme so gedit is;

[PHP]/usr/share/icons/OSX/scalable/mimetypes/gnome-mime-text-plain.png[/PHP]

---

### Post by Irony on 2006-04-14
Unless you mean icons individually rather than groups - in which case right click on the icon select basic tab then select custom icon and choose an icon.

---

