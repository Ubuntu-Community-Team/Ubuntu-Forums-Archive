---
title: "How do I backup firefox bookmarks?"
date: 2009-05-25
forum: General Help
---

### Post by castlefox on 2009-05-25
How do I backup firefox bookmarks?

Where are they saved by default on my computer?

---

### Post by kaibob on 2009-05-26
> **castlefox said:**
> How do I backup firefox bookmarks? Where are they saved by default on my computer?
The bookmarks are stored in:

/home/username/.mozilla/firefox/uniquename/places.sqlite

I just copy this file to a backup location and then copy it back to restore if needed. If you want something designed for the purpose, I'm sure other forum members will recommend a utility or Firefox extension.

---

### Post by lisati on 2009-05-26
I use the Xmarks add-on to keep the bookmarks synchronized between my machines - it's also useful as an automated backup.

---

### Post by castlefox on 2009-05-26
I dont see the .mozilla folder in my folder tree

---

### Post by merlinus on 2009-05-26
Make sure hidden files are viewable.  Ctrl-H will do this, or View/Show Hidden Files.

---

### Post by castlefox on 2009-05-26
Thanks for the control+H tip merlinus

---

### Post by Animemike on 2009-05-26
> **lisati said:**
> I use the Xmarks add-on to keep the bookmarks synchronized between my machines - it's also useful as an automated backup.

Agreed Xmarks is a very good add-on and all free give it a try :KS

---

### Post by dhughes on 2009-05-26
The easiest way is to open Firefox:

 Bookmarks>Organize Bookmarks>Import and Backup>Backup>Boomarks [current date].json is created

 Rename the "Boomarks [current date].json" if you like and then save that file, to restore just do the same thing on choose Restore and select the .json file.

---

### Post by meet.aman7 on 2009-05-26
U can also export the list of your bookmarks as a HTML file by selecting 

Bookmarks>Organize Bookmarks>Import and Backup>Export HTML.

I find this neater cause its in a **human readable format**.

---

### Post by Donalb on 2009-05-26
I've been using Xmarks, (previously Foxmarks) for 2 years. As said above, it's a free Firefox addon. It will back up your bookmarks online where you can also access them, and will also synchronize them across machines. It's perfect for moving to a new machine or synchronising between a work and home machine, or all machines in one house etc. It also backs up passwords.

---

