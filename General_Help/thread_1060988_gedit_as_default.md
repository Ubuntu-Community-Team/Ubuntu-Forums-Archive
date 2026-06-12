---
title: "gedit as default"
date: 2009-02-05
forum: General Help
---

### Post by sigutis on 2009-02-05
Hello, I am using ubuntu 8.04 with gnome. I am doing some programming and its tedious when I am being asked **Do you want to run ***** or display its contents?** when I click on a text file. I have to select **Display ** every time and that makes little sense to me.

So I was wondering if there is a way to make gedit open text files automatically after double click?

---

### Post by pnutzh4x0r on 2009-02-05
The problem is probably that your source file is marked executable, so nautilus doesn't know whether to run it or or allow you to edit it.  The work around for this is to simply mark your text file non-executable and it will open in gedit when you double click it. 

If you are opening files off a FAT/NTFS partition, then this is more difficult to work around, because by default all files on these types are partitions are marked executable.  More information can be found about this issue here:

[https://bugs.launchpad.net/nautilus/+bug/14335](https://bugs.launchpad.net/nautilus/+bug/14335)
[http://bugzilla.gnome.org/show_bug.cgi?id=313023](http://bugzilla.gnome.org/show_bug.cgi?id=313023)

---

### Post by stchman on 2009-02-05
> **sigutis said:**
> Hello, I am using ubuntu 8.04 with gnome. I am doing some programming and its tedious when I am being asked **Do you want to run ***** or display its contents?** when I click on a text file. I have to select **Display ** every time and that makes little sense to me.

So I was wondering if there is a way to make gedit open text files automatically after double click?

Yes, the 2nd poster is correct.  Your programs source has been made executable.  If you are programming scripts then they need to be executable to work.  If you are programming in C or Java then make the source code not executable.

This can be done by right clicking and selecting properties.

---

### Post by regala on 2009-02-05
> **stchman said:**
> Yes, the 2nd poster is correct.  Your programs source has been made executable.  If you are programming scripts then they need to be executable to work.  If you are programming in C or Java then make the source code not executable.

This can be done by right clicking and selecting properties.

yeah, the third poster is correct, when he says that the second poster is right.

---

### Post by mcduck on 2009-02-05
Also take a look in file manager's settings, on the Behavior-tab you'll find options 3 possible options for executable files:

- Run executable text files when they are opened
- View executable text files when they are opened
- Ask each time

The last one is the default, you'll want to change this to the second option. :)

---

