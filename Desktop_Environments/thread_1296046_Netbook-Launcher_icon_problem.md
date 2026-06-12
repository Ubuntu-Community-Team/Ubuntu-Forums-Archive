---
title: "Netbook-Launcher icon problem"
date: 2009-10-20
forum: Desktop Environments
---

### Post by Morimando on 2009-10-20
Hi there.
I have a problem with netbook-launcher. The problem is as follows: In System (Where there a submenus to the main menu), some icons become too large, meaning their frame stretches beyond the usual depth and thus move the following icons down. The icons in the next row then shove the icons that should be there further down and the end of the list consists of multiple icons that are above and beyond each other, making the one beneath the other almost inaccessible. And what's worst: It looks really shitty when I want to show how neat and nice Ubuntu is compared to Windows.
Steps I took to get rid of the problem:
- removing all entries in .gconf/apps related to netbook-launcher
- removing all entries in .config/ related to netbook-launcher
- completely removing ume-launcher
- completely removing netbook-launcher
- reinstalling netbook-launcher
- moving the complete .gconf/ folder somewhere else and reconfiguring gnome

Alas, none of the steps above changed anything.
Further ideas?

(Screenshot attached to  demonstrate the "stretched" icon borders)

---

### Post by Arjunanda on 2009-10-30
I have this same very annoying problem. Ideas, anybody?

---

### Post by Katalog on 2009-10-30
The only place I have really noticed a similar problem is in the "Games" section where the icon titles on the bottom icons have been pushed off the bottom of the screen. I have no idea what is causing it, but I fixed the problem in the "System" section by unchecking the apps that I don't use (like Accessibility) in the Main Menu preferences so they don't show up in that section. Definitely a problem though, and sounds like it might be something worthy of filing a bug report against, or maybe better yet add to the existing ones about Maximus and the Netbook Launcher not having enough user configurable options.

---

