---
title: "KDE on K/Ubuntu"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Igtenio on 2006-07-05
I hope this's in the right place. Half of it is specifically Kubuntu, whereas the other is just general Ubuntu.

I've known about Ubuntu for a while, but haven't messed with it much. Since I'm partial to KDE, I decided to install Kubuntu instead of regular Ubuntu. However, I found that the KDE desktop used in Kubuntu isn't stock KDE. While I don't really take issue with that(I'm sure there was a good reason for doing such), I'd like to install stock KDE, with no specific Kubuntu branding.

I searched the forums, and came across [this thread](http://ubuntuforums.org/showthread.php?t=148449&highlight=%22Plain+KDE%22) where a question was asked about how Kubuntu-desktop and the KDE packages install too much unwanted software, and a reply said that the best method was to do a server install, and then use apt to get a set of packages.

What I wanted to know was whether anyone knew if this installed the stock KDE packages, without Kubuntu branding, or simply reinstalled select Kubuntu packages without excess ones. I would test it myself, but unfortunetely, I'm on Dialup, and I'd rather not spend hours finding out that the answer.

Second, when using a regular Kubuntu install, is there any method to allow icons to exist on the desktop? Everytime I've attempted to create a link or similar, it might stay for a few moments, but it inevitably disappears. Probably a novice question, but I can't find an answer for it. Although I have no doubt someone'll come along and post a link to the FAQ I've combed over and show me the errors of my assumption that I've looked enough. :P

Thanks for the help.

---

### Post by Jucato on 2006-07-05
1. To install the "stock" KDE, you have a choice to either install the *kde* metapackage, which install [b]all[/]b official KDE stuff (including artworks, icons, games, etc), or *kde-core*, which just installs the base kde/kdelibs packages. However, the settings that will be used will still be Kubuntu's. Meaning, the configs/customizations for some (at least those directly modified by Kubuntu) of the packages will still use Kubuntu's config, AFAIK. 

I'm not so sure about the process of installing pure KDE using a server install.

2. Right-click on the desktop, choose Configure Destkop then Behavior, make sure that the appropriate options are checked. (I'm not in Kubuntu right now, so I can't give specific details/names).

---

