---
title: "Different Menu Systems Inconsistent"
date: 2009-06-17
forum: Desktop Environments
---

### Post by aragilar on 2009-06-17
For GNOME (and I assume KDE from looking at the contents of the files and folders) *.desktop, where * is the name of the program/package, determine the menu entries. These are located in /usr/share/applications/.

For Fluxbox, the files in /usr/share/menu/ determine the entries in the menu.

The problem is some packages (I noticed Prism and it associated webapps to be one) have an file in only one of these locations, meaning that it only appears in one menu system.

Can someone explain why Ubuntu has both these systems?

---

### Post by coffeecat on 2009-06-17
I can't be sure, but I think it goes something like this.

Ubuntu has to integrate as best it can various independent upstream projects. All the major desktops are such upstream projects. The two major desktops (gnome and KDE) have completely different underlying structures and engines, but the KDE and gnome developer teams do a very good job of ensuring that native gnome apps and native KDE apps run in the "other" desktop. I guess that's true of menu entries too, because you'll find that the actual menu configuration files for gnome or KDE will be in (different) hidden files in your home folder. 

Gnome and KDE (and Xfce) are officially supported by Canonical, the company behind Ubuntu, so the Ubuntu devs try to ensure that all Ubuntu supported apps (in the main and restricted respositories) integrate well into the Ubuntu supported desktops. Fluxbox is not officially supported (as far as I can make out) and Prism is in the Universe repository which is not supported by Canonical - it is described as "community maintained". 

> **aragilar said:**
> Can someone explain why Ubuntu has both these systems?

So, to answer your question, it's not Ubuntu that has both these systems. Both fluxbox and prism come from independent developers or teams of developers. You'd need to put your question to them, or to the developers of any other app that doesn't integrate well.

---

