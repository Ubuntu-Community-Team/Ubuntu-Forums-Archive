---
title: "Resize Filesystem?"
date: 2009-03-13
forum: General Help
---

### Post by xHalloweenx on 2009-03-13
I need to resize the ubuntu file system from 10gb to 30gb.
How would I go about doing so?

Also I keep getting this error for some themes and for compiz

Window manager warning: Failed to load theme "default": Failed to find a valid file for theme default

---

### Post by LegendofTom on 2009-03-13
You could install gparted and use that as a frontend to resize.

---

### Post by stanz on 2009-03-13
Yeah...thats an easy/simple program ~ boot to it and make your changes ~*
Always painless results.

:)

---

### Post by Tobywuk on 2009-03-13
+1 for gparted, its what I use. It is a nice program that gives you a friendly GUI for resizing, deleting and adding partitions.

to install 
```
sudo apt-get install gparted[/url]

remember when you run the program (by typing 'gparted' in the terminal) you need to use [code]sudo gparted
```

You can also resize and alter partitions using the terminal and fdisk, although dont ask me how.

---

### Post by xHalloweenx on 2009-03-13
If someone could tell me how to do it via terminal taht would be great.
gparted didnt work for me.

---

### Post by xHalloweenx on 2009-03-13
Updated first post, another problem added

---

### Post by stanz on 2009-03-14
> **xHalloweenx said:**
> If someone could tell me how to do it via terminal taht would be great.
gparted didnt work for me.

The simplest way I found to use gparted--
-is to burn the '.iso' to a cd 
-reboot to it, hoping the BIOS will boot from your cdrom
[os isn't running/mounted]
-choose gparted [once fully loaded] and make your changes! 

What version of Ubuntu ya running?
gparted .iso: [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779")
old instructions with pictures: [here]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")  I don't think its changed to much.
an on-going forum thread: [here]("http://ubuntuforums.org/showthread.php?t=282018&highlight=gparted")

---

### Post by stanz on 2009-03-15
> **xHalloweenx said:**
> Also I keep getting this error for some themes and for compiz
Window manager warning: Failed to load theme "default": Failed to find a valid file for theme default
oww-- compiz.
Have ya googled for that one?
Checked over the "Desktop Environments" Threads?
Ya may need to just adjust some settings there...

---

### Post by chubble10 on 2009-03-15
could try using a partition manager in (dare I utter the word...):shock: Windows:shock: you can get loads from any good PC magazine. (That is if you still or ever had :shock:Windows:shock:)

---

### Post by Slim Odds on 2009-03-15
Just use the Ubuntu Live CD, it has gpartd already.

---

