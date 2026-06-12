---
title: "Can't Make Trash Icon Appear"
date: 2008-10-22
forum: Desktop Environments
---

### Post by pirattrev on 2008-10-22
I've been using Ubuntu as my sole computer for a while (no windows whatsoever) but a throwback to mac and windows was to have "The Trash" icon on my desktop.  However, a little while ago the icon (which I'd enabled though gconf-editor) now longer appeared.  I hadn't changed the icon set, and it wasn't hidden off the screen and yet in gconf it claimed that there should be an icon on my desktop for "The Trash". The Network, Home, Mounted Filesystems, and Computer icons still appear, but not the trash. Any help or suggestions to test?

---

### Post by kilroy423 on 2008-10-23
The trash icon is just a link to 

/home/USERNAME/.local/share/Trash/files/
/home/USERNAME/.local/share/Trash/info/

you could just create symlinks on your desktop to that folder or you can right click on one of your panels>add to panels>trash

---

### Post by pirattrev on 2008-10-23
i know how to have the trash on panels, but that's not the problem.  The issue is that I'd like to have The Trash on my desktop, and fundamentally I'd like to solve the gconf-editor issue rather then just pull off a simple hack for it.  If anyone actually knows what the problem/bug is, please tell. Not so much looking for a way around it but a solid solution. This is actually a problem a lot of people have been having so it'd be cool if someone has some insight.

---

### Post by pvalley1967 on 2008-10-23
press "alt-F2" type gconf-editor click on apps>nautilus>desktop then select trash and click the box next to it

---

### Post by swisscow on 2008-10-24
> **pvalley1967 said:**
> press "alt-F2" type gconf-editor click on apps>nautilus>desktop then select trash and click the box next to it

The OP has done this. 


Try changing your theme. Perhaps the trash icon has gone??

---

### Post by pirattrev on 2008-10-30
> **swisscow said:**
> The OP has done this. 


Try changing your theme. Perhaps the trash icon has gone??

No luck on that suggestion, thanks though. Any other ideas? I'm fresh out. I've tried to set the trigger with sudo privileges, by turning it off and then rebooting before turning it on, I've even checked all the icon names to make sure there wasn't an error.

---

