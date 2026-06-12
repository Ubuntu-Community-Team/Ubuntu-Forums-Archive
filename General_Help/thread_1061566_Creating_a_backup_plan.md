---
title: "Creating a backup plan"
date: 2009-02-05
forum: General Help
---

### Post by Abused on 2009-02-05
I believe there is a way to compile a .tar or .rar or .zip file of some sort containing all of your backup files, and then you can run a terminal command simply to update all the files on it when they have been altered, or only to add the new files?

I'd like to do this because at the moment the only way for me to add new files to my backup, or to update files that I have changed is by dragging them in manually, and it gets quite tiresome (and I'm also worried I'll forget one). 

I hope my request is clear. If you need me to elaborate, please just say. Also, I am backing up to an external hard drive (/media/FreeAgent Drive), if it is of any importance.

---

### Post by pytheas22 on 2009-02-05
You're probably thinking of rsync, which copies only files that are new or have been modified.  The usage is pretty straight-forward if you read the man page, and I believe there are some graphical frontends available in the repositories if you search.

---

