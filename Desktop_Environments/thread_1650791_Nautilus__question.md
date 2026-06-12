---
title: "Nautilus  question"
date: 2010-12-22
forum: Desktop Environments
---

### Post by gprec on 2010-12-22
Newbee Ubuntu user here, I have a little bash question related to Nautilus.
Say for example I have a list of some directory paths, I would like to find some sort of command for use in terminal in form

  command path1 path2....path_k

and as a result to open all directories in a single Nautilus window, each directory in separate tab.
Thanks and sorry for my english.

---

### Post by gprec on 2011-05-30
I recently discovered pcmanfm and, from what I saw, the command

pcmanfm directory_1 directory_2 ... directory_k

open as tabs all these directories  into pcmanfm's current instance.

I like the idea of &#8203;&#8203;a file manager that allows work in a "single instance" mode, just like firefox or gedit
Some people (me included) tend to be very disorganized in the computer work, for example, 
I almost always end up having wasted tens of nautilus windows on the desktop. 
The "single instance" mode can force you to work in a cleaner manner
Unfortunately, it seems not so easy to completely replace nautilus with pcmanfm,
but this can be achieved partly by editing the files "nautilus-folder-handler.desktop" and "nautilus-browser.desktop. 

Pcmanfm is also much faster compared with nautilus but it also has disadvantages. 
For example, it has only limited support for user actions and seems to miss completely an internal search function

---

### Post by Krytarik on 2011-05-30
> **gprec said:**
> 
Pcmanfm is also much faster compared with nautilus but it also has disadvantages. 
For example, it has only limited support for user actions and seems to miss completely an internal search function
+1 regarding its fastness

How is "Tool -> Find Files" then!? ;-)
Even much better than Nautilus' built-in search feature.

Greetings.

---

### Post by gprec on 2011-05-31
Thanks for the tip, but my version (0.9.9) don't have this option, tools menu has only 
two entries ("Open current folder in terminal"  and  "Open current folder as root" )
though I am sure that this feature will be added sooner or later. 
In the meantime I can use an external tool as gnome search tool or locate, even if a little awkward
A quick filter box (live filter) for the current directory would be ideal for me but this kind of feature is not very common for Linux 

Overall, I'm happy with pcmanfm, primarily due to its "single instance" mode and also its excellent speed

---

### Post by Krytarik on 2011-05-31
> **gprec said:**
> Thanks for the tip, but my version (0.9.9) don't have this option, tools menu has only 
two entries ("Open current folder in terminal"  and  "Open current folder as root" )
though I am sure that this feature will be added sooner or later. 

That's weird, I'm using version 0.5.2, and it is there! That means that those feature must have been removed since then.

---

