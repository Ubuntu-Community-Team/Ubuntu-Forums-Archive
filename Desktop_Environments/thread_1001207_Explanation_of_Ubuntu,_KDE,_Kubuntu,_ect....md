---
title: "Explanation of Ubuntu, KDE, Kubuntu, ect..."
date: 2008-12-03
forum: Desktop Environments
---

### Post by NitroStar on 2008-12-03
Hello, I have read and terminaled and hunted for several hours now. I am confused. Someone please explain:

I installed Ubuntu Intrepid 8.1. I thought I installed KDE 4.1.2 on top of it (I was told to install it over Ubuntu, then I could boot into KDE or Ubuntu. I can, but I have since learned that there is  difference between Gnome Desktop Manager, and KDE desktop manager and these are different from the Window managers. KDE doesn't work just right. I installed it by one of the package managers and selected KDE. The "Folder View" widget is missing in KDE. I've read more and think that I was supposed to install Kubuntu instead of just the KDE. I'm not sure and didn't find specific instructions on the KDE website. KDE is missing Konquerer, Adept package manager, and other things also. Are they supposed to be missing the way I have it installed? I am very confused about the different KDM, GDM, and Window managers, and really everything. 

Ps. I can't remember when, but at some time the Grub installer added another boot option and the difference is only the last digit in the version. It's something like 8.0.1.something -7 and then 8.0.1 something-9. What is this about? I've booted into both and just notice the same thing under system monitor. Sorry so long, I may ask some of these again if they don't get answered unless I'm directed to a place that explains all of this. I think I understand just enough to make it all muddy!!! Thanks a lot.

---

### Post by __Ryan__ on 2008-12-03
**Ubuntu** uses **Gnome desktop**
**Kubuntu** uses **KDE desktop**

The **window manager** is separate from the desktop as it handles rendering the look of the windows, borders, etc.

If you want KDE you should install Kubuntu over Ubuntu or uninstall **ubuntu-desktop** and install **kubuntu-desktop** packages in Ubuntu. These are catchall meta packages which include not only the desktop but the applications and other goodies that come bundled with them.

These meta packages are the difference between Ubuntu and Kubuntu.

There is a third option, I believe you can install **kdebase** package and have both installed at the same time.

---

### Post by NitroStar on 2008-12-03
I installed kde base. I want to be abble to choose both GNOME or KDE but KDE is missing some features.

---

### Post by jacksaff on 2008-12-04
KDE and Gnome are hugely complex pieces of software. As with most of the open source world each individual piece is designed so that it can be used independently by whoever and whatever needs it. Each piece gets 'packaged'- bundled up with instructions that the system understands and which tell it how the software should be installed and used.

So you don't need to go and find all of these packages yourself there are also metapackages - packages that are just lists of other packages. If you install one, the system knows that it should go find and install everything in the list. 

There are metapackages for all sorts of use cases. If you want just the basic KDE you can install kde base. If you want everything that is included in kubuntu by default, install kubuntu-desktop. Kubuntu doesn't include by default all of the kde packages such as kde-games so you can install all of those aswell. They wouldn't fit on a cd if kubuntu has everything.

Once you have kde installed (whether a minimal install or the lot) you get to it by logging out and selecting kde as a session type in the log-in manager. If you started with ubuntu your log-in manager will be gdm.

---

### Post by NitroStar on 2008-12-04
> **jacksaff said:**
> Kubuntu doesn't include by default all of the kde packages such as kde-games so you can install all of those aswell. They wouldn't fit on a cd if kubuntu has everything.

Once you have kde installed (whether a minimal install or the lot) you get to it by logging out and selecting kde as a session type in the log-in manager. If you started with ubuntu your log-in manager will be gdm.

     I started with ubuntu and know how to change my default desktop manager (not just my session) with: sudo dpkg-reconfigure gdm . I realize there are tons that can be added to linux using the packages, but what I'm trying to say is that the Folder view widget (which is a huge part of the new KDE desktop and was available when I had Kubuntu installed on a separate partition) is not available when I right click and choose "add widgets" and the dialog pops up. It is not in the list. From what I read on the KDE web site, this is part of KDE, not only Kubuntu. When I drop a folder onto the desktop, it just becomes an icon not a folder view. 
     Another thing. Am I better off repartitioning my drive and doing 2 separate installs of Ubuntu and putting Kubuntu over one of them (like I started out with) if I am going to compare Gnome & KDE to decide which one I am going to stick with? Because I notice every thing I install in a Gnome session (after switching to GDM too) is available in the KDE session (after switching to KDM also). But some of the key KDE items (that are features bragged about on the front page of KDE's website are not there, like Dolphin (KDE's filemanager), Konqueror (KDE's webbrowser), but I think the new Phonon multimedia backends for GStreamer makes the system sounds not work right. I hope I explain myself well enough.
What happens if I install Kubuntu onto my Ubuntu? Will I be able to choose which version I want to run or will it convert Ubuntu into Kubuntu only? These are really too many questions I know. Maybe I need to number them so I can check them off. LOL

---

### Post by NitroStar on 2008-12-04
Wait a minute.... I have found a site called psychocats.net. Very simple instructions and explanations to what I am dealing with. I'll let yall know what else I can't figure out. I'm sure there will be something :)!

---

### Post by NitroStar on 2008-12-04
Very useful tutorials indeed!!! [http://psychocats.net](http://psychocats.net)  :D

---

