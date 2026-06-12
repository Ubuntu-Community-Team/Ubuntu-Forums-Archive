---
title: "oneiric gnome system menu hidden by date"
date: 2011-10-26
forum: Desktop Environments
---

### Post by marfie on 2011-10-26
Upgraded from 11.04 and had to work on getting multiple VNC sessions working again. (Simple in the end.) As part of this I installed gnome fallback but now, on both the console and wider screen VNC sessions, the system menu in gnome is covered by the central date banner background.

The ~/.vnc/xstartup file has 

[FONT=Courier New]exec gnome-session-fallback &[/FONT]

I think I either need to know what to replace this with so the VNC sessions use unity or to fix the issue with the system menu being covered in gnome.

Can someone give me some pointers please? If I need to change the gnome config please tell me how to get to it because the menu is not there :)

Cheers

Paul

Edit: I have been looking round some more and seen postings suggesting that there is no longer a System menu - just Applications and Places. Oh. My bad.

---

### Post by crdlb on 2011-10-26
> **marfie said:**
> 
Edit: I have been looking round some more and seen postings suggesting that there is no longer a System menu - just Applications and Places. Oh. My bad.

Some of the other changes in the fallback session are covered here: [https://help.ubuntu.com/community/GnomeClassic](https://help.ubuntu.com/community/GnomeClassic)

---

