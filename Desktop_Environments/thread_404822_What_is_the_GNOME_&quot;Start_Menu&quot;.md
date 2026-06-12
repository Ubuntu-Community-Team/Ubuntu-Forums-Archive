---
title: "What is the GNOME &quot;Start Menu?&quot;"
date: 2007-04-08
forum: Desktop Environments
---

### Post by tcv on 2007-04-08
Hey folks,

I am enjoying Ubuntu Edgy on my Sony laptop.

I'd like to know more about how GNOME stores items for its "Start Menu," to use the Windows phrase. As many of you know, in Windows this is a simple collection of directories and shortcuts under C:\DOCUMENTS AND SETTINGS\%USERNAME%\Start Menu\.

But how is this done in GNOME?

For those of you that are paying real close attention, I am going to post this at LinuxQuestions, too. I sure hope that's okay.

Thanks,

Mike..

---

### Post by rennen01 on 2007-04-08
I don't know if this is gonna help, but

System > Preferences > Menu Layout

allows to choose what is displayed in the Applications/Places/System Toolbars

GL

---

### Post by tcv on 2007-04-08
Oh, I know how to edit it. I'm more interested in how it's structured underneath. 

Thanks!!

---

### Post by lexxonnet on 2007-04-08
> **tcv said:**
> Oh, I know how to edit it. I'm more interested in how it's structured underneath. 

Thanks!!
KDE stores it as a bunch of .desktop files in a certain directory. Each one has meta data which says which folder it belongs in, and the link it points to. I believe gnome shares a similar structure

---

### Post by ComplexNumber on 2007-04-08
> **tcv said:**
> Oh, I know how to edit it. I'm more interested in how it's structured underneath. 

Thanks!!
you'll find some of it in ~/.local, and some of it in ~/.gconf/desktop/gnome/applications/main-menu

---

### Post by hikaricore on 2007-04-09
Both gnome and kde make this more of a mess than it needs to be.
There are configuration files and subconfiguration files and .desktop files in multiple directories.

I advise modifying items through the menu editors, I've killed my menus before trying to manually modify the contents.

---

