---
title: "Ubuntu 11.04 - Gnome - Nautilus - &quot;No templates installed&quot;"
date: 2011-07-01
forum: Desktop Environments
---

### Post by dlogan on 2011-07-01
In Nautils, when I right-click, and go to "Create Document", it says "No templates installed".

Searching, I found a thread from 2006 about this.  The solution was simply to create some empty Office docs and put them in ~/Templates.  I tried created an empty spreadsheet and writer documents and put them in my home directory in the Templates folder. That didn't change anything.

So, what am I missing?

Sorry, I'm new to Ubuntu, I've been doing Gentoo for years but finally got tired of updates breaking everything and it taking forever to fix it :)

---

### Post by varunendra on 2011-07-02
> **dlogan said:**
> In Nautils, when I right-click, and go to "Create Document", it says "No templates installed".

Searching, I found a thread from 2006 about this.  The solution was simply to create some empty Office docs and put them in ~/Templates.  I tried created an empty spreadsheet and writer documents and put them in my home directory in the Templates folder. That didn't change anything.

So, what am I missing?
Apparently "nothing"! This works in my 10.04 and 10.10, so it maybe some bug in 11.04 it seems. If you are using Unity, then try changing to classic GNOME desktop from login screen and see if it works. I personally have no experience with 11.04 though.

By the way, don't you have the option to create an 'Empty file' in the same right-click menu?

---

### Post by dlogan on 2011-07-13
I am already using the classic gnome, I didn't care for the Unity interface.  Yes, there is a button to create an empty file in that menu.

---

### Post by varunendra on 2011-07-13
> **dlogan said:**
> .. Yes, there is a button to create an empty file in that menu.
Well, then you can just create an empty file, rename it to whatever you wish, then add suitable extension name to match the file type you want to create.

I used to do the same thing until I got the ~/Templates trick. Although not a solution, but it works.

---

### Post by dlogan on 2011-07-13
I actually tried that.  I create an empty file, like asdf.xls

The extension correctly associates the file w/ LibreOffice.  When I double-click to open it, the Libre splash screen comes up like it's loading, then it just goes away.  I have to open LibreOffice Calc from the Applications menu and create a new spreadsheet.

I realize this isn't the worst problem in the world to have, but it would be convenient if this worked properly.

---

