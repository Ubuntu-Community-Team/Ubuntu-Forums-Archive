---
title: "GTK Styles and Fonts"
date: 2005-07-10
forum: Desktop Environments
---

### Post by henderson63 on 2005-07-10
This should be under Appearance etc in the KDE Control Centre.

It's not there.

I'm using the sources.list that was installed, but I can't find
gtk-qt-engine which I understand is required for the above.

Any suggestions gratefully accepted.

D

---

### Post by harry on 2005-07-10
Use gtk2-engines-gtk-qt

---

### Post by SysFail on 2005-07-11
I think you said you were using the "default" sources.list file.  The gtk engine is in universe...you need to edit your sources.list.

---

### Post by darkfox on 2005-10-02
I've installed this.  It appears in roots KDE session (kcontrol >> Appearance), and for each of the users I do administration for on the same machine, but it does not appear in my session.  Any ideas - its driving my nuts?!  I've removed my KDE directory completely and had it rebuilt, but still the same thing.

---

### Post by mlomker on 2005-10-02
[QUOTE=darkfox]I've installed this.  It appears in roots KDE session (kcontrol >> Appearance)[/QUOTE]

I assume you've tried reinstalling the package?  If you look at the installed files the applet seems to be /usr/share/applnk/Settings/LookNFeel/kcmgtk.desktop

It can be executed from the Run Command line: **kcmshell kcmgtk**

---

### Post by jbuberel on 2005-10-16
So what if the command to launch this fails, indicating that the kcmgtk plugin is not available? I am running ubuntu/kubunte breezy badger 5.10 release, and everything appears up-to-date:

> kcmshell kcmgtk
kcmshell (kdelibs): WARNING: Could not find module 'kcmgtk'.

I've searched through adept/synaptic for a package that might provide the kcmgtk plugin, but nothing seems obvious to me. Any suggestions?

Thanks,
jason

---

### Post by mlomker on 2005-10-16
[QUOTE=]So what if the command to launch this fails, indicating that the kcmgtk plugin is not available? [/QUOTE]

The discussion was about the **gtk2-engines-gtk-qt** package.  They renamed it to **kcmgtk-xdg** in Breezy.

---

### Post by jbuberel on 2005-10-16
With a sources.list that looks like this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse

And after doing an 'apt-get update', followed by:

> apt-get install kcmgtk-xdg

I'm told that there is no such package. Did I misunderstand what you posted?

Thanks,
jason

---

