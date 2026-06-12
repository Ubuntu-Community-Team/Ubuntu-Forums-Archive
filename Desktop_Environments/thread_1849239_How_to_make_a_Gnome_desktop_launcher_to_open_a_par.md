---
title: "How to make a Gnome desktop launcher to open a particular spreadsheet."
date: 2011-09-24
forum: Desktop Environments
---

### Post by scruffyeagle on 2011-09-24
I came here to share, because I felt pretty cool figuring it out. I'm going to go into detail about it, because there might be some other Linux newbies that don't know how to do this, and the why of the parts.

Before diving into Linux this summer, I was a long-time user of Windows. I didn't realize how much I leaned on the ability to make a "shortcut" that would launch a particular document for editing, until I got into Gnome and didn't have that utility readily available. Using the file manager, I've found that I couldn't make a link that would launch a spreadsheet. It told me that links couldn't be made for that kind of item. In Gnome, the menu-click on the desktop lets you make a "launcher". Usually, that means a way to launch a program. But, I adapted it for launching my spreadsheet.

Using the Main Menu utility from the Preferences menu, I checked the properties of the Open Office Spreadsheet program. I found the command for launching it was
```
ooffice -calc %F
```

I used this as my template for creating a command to launch my spreadsheet. The first part is the command for launching the Open Office program. The second part specifies which module to use. The 3rd part is a variable that can be filled with a file name (placed there instead of "%F".)

Creating my launcher on the Gnome desktop, I typed in "Budgeting Spreadsheet" as the name. I typed in "Open the current budgeting spreadsheet." as the description (the "Comment" field in the dialog box). Then for the "Command" field, I specified which program to use, followed by the full path name leading to my spreadsheet as the file name variable. Using the full path name was the real trick.

I don't like posting online the real names of my directories, for fear of hackers, so I'll be substituting names that are similar - but, a key to getting this to work was the use of quotation marks within the path name. I have an external HD that was used under Windows, and many of the directory names contain blank spaces. Within a Linux command, a space is interpreted as separating parts of the command. Quotation marks make it possible to use spaces inside a command without them being interpreted that way.

An important thing to know about this, is about how to find your external HD in the filing system. Since my spreadsheet is on an external HD, it gets mounted into the filing system when Gnome starts up as a subdirectory of the "media" directory. Therefore, my full pathname starts by specifying that. Here's an example of the command for launching Open Office to open a spreadsheet from a subdirectory on an external HD:
```
ooffice -calc /media/"LOTSA DATA"/economics/Budgets/"Current Budgeting.ods"
```

Pretty cool, huh?

---

### Post by staticd on 2011-09-24
> Using the file manager, I've found that I couldn't make a link that would launch a spreadsheet

Right click on "Current Budgeting.ods"->make link.
Wont work on Fat pendrives cause they dont support symlinks.
try```
 ln -snf src dest
```

---

### Post by staticd on 2011-09-24
Oops! too much terminal from me. Just middle click and drag your file to where you want to create a link. eg your desktop.

---

### Post by vasa1 on 2011-09-24
> **staticd said:**
> Oops! too much terminal from me. Just middle click and drag your file to where you want to create a link. eg your desktop.

What's an alternative to middle-click?

---

### Post by Krytarik on 2011-09-24
> **vasa1 said:**
> What's an alternative to middle-click?
Hold down the Alt key while dragging the concerning item/s (you will notice a "?"-emblem beneath your mouse pointer). When releasing the mouse button, a context menu pops up, where you can choose "Link Here"; the other options are "Move Here", "Copy Here", and "Cancel".

Greetings.

---

### Post by vasa1 on 2011-09-24
> **Krytarik said:**
> Hold down the Alt key while dragging the concerning item/s (you will notice a "?"-emblem beneath your mouse pointer). When releasing the mouse button, a context menu pops up, where you can choose "Link Here"; the other options are "Move Here", "Copy Here", and "Cancel".

Greetings.

That doesn't seem to work for me :(

When I hold down the Alt key and try and drag anything, the Nautilus window moves!

I can just right-click on any file and then I get the option to make a link. It makes a link in the same folder which I can then drag to the desktop.

Maybe it's because I'm on 11.04?

Edit: just noticed this is a gnome topic! I'm using Unity. My bad!

---

### Post by Krytarik on 2011-09-24
> **vasa1 said:**
> When I hold down the Alt key and try and drag anything, the Nautilus window moves!
[..]
Edit: just noticed this is a gnome topic! I'm using Unity. My bad!
 Start dragging the concerning item/s, and only then press the Alt key.

And Unity is based on Gnome, it's just a plugin of Compiz.

---

### Post by scruffyeagle on 2011-09-26
> **Krytarik said:**
> Hold down the Alt key while dragging the concerning item/s (you will notice a "?"-emblem beneath your mouse pointer). When releasing the mouse button, a context menu pops up, where you can choose "Link Here"; the other options are "Move Here", "Copy Here", and "Cancel".

Greetings.

Thanks for the tip! I'll give it a try.

---

### Post by alicon on 2011-10-08
Thanks for posting. That is exactly what I was trying to do. I used libreoffice -calc "file_name". Worked like a charm!

---

### Post by scruffyeagle on 2011-10-14
> **alicon said:**
> Thanks for posting. That is exactly what I was trying to do. I used libreoffice -calc "file_name". Worked like a charm!

You're welcome! I'm pleased, that I was able to be of service to you.

---

