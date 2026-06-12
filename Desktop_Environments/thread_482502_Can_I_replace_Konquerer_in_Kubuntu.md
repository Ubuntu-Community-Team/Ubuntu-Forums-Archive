---
title: "Can I replace Konquerer in Kubuntu?"
date: 2007-06-23
forum: Desktop Environments
---

### Post by Nazosan on 2007-06-23
I love Kubuntu, but the use of Konquerer as the file manager is killing me.  I swear it has every single one of the worst aspects of Microsoft Explorer and not a single one of the good aspects...  I can't even find an option to disable single click activation (as opposed to the standard of double clicking) which makes doing things like selections a lot harder for no valid reason...  I've always loved KDE, but the fact that most things have it using Konquerer by default has always been one huge black mark against it for me...  Preloading (by default anyway) and integrated non-removable support for web browsing?  Ugh...

Having never done this before, I don't really know what alternatives are out there.  Really I want something a little like Explorer, but with at least some of the good features of it.  As I recall, the default that came with GNOME in Ubuntu wasn't half bad for example.  But besides not knowing what options there are, I have no idea how one would change it to be the default such that it could handle things like when I run "/media/whatever" for example.  I'd really find it inconvenient and annoying to have to manually start it and then point it to the location I want...

Sorry for something of a newbieish question here, but I don't even know how to start on such a thing.  Konquerer is driving me insane though...

---

### Post by {spitFire} on 2007-06-23
You can obviously use other file managers like Nautilus or Thunar, but IMHO I guess then you have to load the appropriate desktops as well (or at least the desktop libs associated  to the app). I however, don't know how to make it the default.

---

### Post by Nazosan on 2007-06-23
> **{spitFire} said:**
> You can obviously use other file managers like Nautilus or Thunar, but IMHO I guess then you have to load the appropriate desktops as well (or at least the desktop libs associated  to the app). I however, don't know how to make it the default.

That's what I figured too, though I really don't want to add unnecessary things considering that harddrive space is becoming critical here...  Then too, if it's not default, it may be just tedious enough to make Konquerer worth putting up with until I can figure out how to switch it anyway.  If someone knows how to do all of this, I'd really appreciate it if they could tell me which libraries are required so I can add just those.

---

### Post by Happy_Man on 2007-06-23
Actually, you can disable the single-click behavior somewhere in Kcontrol. Not sure I remember where, though.....

Although, if you really hate Konq, you can try Dolphin. It's the new filemanager for KDE 4. Should be somewhere on the internet...

---

### Post by dashun on 2007-06-24
> **Nazosan said:**
> ... I can't even find an option to disable single click activation (as opposed to the standard of double clicking) which makes doing things like selections a lot harder for no valid reason...

KDE Control Center (kcontrol) -> Peripherals -> Mouse -> General -> Icons
Select "Double-click" option instead of "Single-click"

> **Nazosan said:**
>  ...and integrated non-removable support for web browsing?  Ugh...

As the above poster mentioned, there will be a new file manager in KDE4 called Dolphin, which will compliment Konqueror. Unlike Konqueror, Dolphin will mainly focus on being a file manager (i.e not a web browser too). The beta KDE3 version of Dolphin is available in the repos.

---

### Post by ricardisimo on 2008-06-11
Dolphin behaved itself just fine until I installed the KDE4 desktop. Dolphin for KDE4 insists on single-click activation instead of double-click. Anyway to change that within dolphin?

---

### Post by Happy_Man on 2008-06-11
Same way you changed it in KDE3 - Kcontrol.

---

