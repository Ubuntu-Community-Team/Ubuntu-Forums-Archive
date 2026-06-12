---
title: "Lucid doesn't Boot on HP HDX 18"
date: 2010-04-05
forum: Development CD/DVD Image Testing
---

### Post by WitchCraft on 2010-04-05
Lucid doesn't Boot on HP HDX 18 Notebook.

The normal beta install cd crashes, you can select the language, but it doesn't get any further. Black screen for all eternity.

Nvidia Gforce 9600 GM ...

---

### Post by ajgreeny on 2010-04-05
Is it a bad iso or burn?  Check the md5sum of the iso file you have against the listed md5sum, and burn at no more tha x4 speed.

---

### Post by monkeyface766 on 2010-08-21
No its not the disk. I have a HDX and I'm pretty sure that there is a problem between the video card and Lucid. To get past the blank screen of eternity, do the following:

[LIST=1]
[*]Boot into installer disk
[*]Key down and hover over the "install ubuntu" menu item
[*]use the hotkey (F6 i think?) to edit the boot options
[*]the last two strings on the boot line will say "splash something..."
[*]delete those two end strings and type in "nomodeset"
[*]then hit enter and the install will work
[/LIST]

---

