---
title: "Locking a DE into single-application usage?"
date: 2007-02-23
forum: Desktop Environments
---

### Post by Ed Ropple on 2007-02-23
Hey there, folks.

Long-time Linux user, decently oldfashioned Ubuntu user (Warty for the win). Got a bit of a question for you all, and I'm hoping you guys can help me out!

I write software in .NET and am looking at porting it over to Linux (thank you, Mono project!). One of my applications is a network-based point-of-sale system. Under Windows, it runs on a normal copy of XP with a registry hack to run my program in place of the explorer.exe desktop. I'm looking to do the same in Linux. Can someone point me toward resources that might help me lock down a desktop environment for very strict single-application usage?

What I'm envisioning is just the very basics of the windowing manager, only enough to run a GTK+-based application. No panels/kickers, no menus, nothing--only one application, and if for some reason it segfaults out, start it back up (though I imagine I'll have to handle that outside the DE itself, and I can do that myself for certain).

As Mono uses GTK+, GNOME or XFCE are probably the best bet. I'm a KDE man myself, though, so if anyone has particularly slick instructions for this for KDE, I won't shed too many tears. ;)

Thanks in advance for your help!

err

---

