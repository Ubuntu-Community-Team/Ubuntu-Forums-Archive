---
title: "KDE Session Does Not Load"
date: 2005-12-20
forum: Desktop Environments
---

### Post by Scabby_al on 2005-12-20
Just installed a brandy new copy of Breezy and I installed the Nvidia drivers and made the appropriate changes to xorg. I also been tooling around and customizing my desktop just how I like it. Now, when I log into KDE, it hangs at "Restoring Session". Is there a way to delete my previously saved session so I can log in?

---

### Post by localzuk on 2005-12-20
I am not specifically sure about which files you need to remove but all the kde settings are stored in the directory .kde in your home directory.

---

### Post by Cathbard on 2005-12-20
The simplest way is to move the files out of the **~/.kde/share/config/session/** folder.
You can try moving one at a time so you can identify which one hangs the machine too.

---

### Post by Scabby_al on 2005-12-20
No luck. Still hangs at 0% at the "Restoring Session" splash screen.

---

### Post by Cathbard on 2005-12-21
If you rename the .kde folder you should be presented with the startup wizard next time you log in. That will create a new .kde folder.
Personally I think the "restore previous session" option in kde is too dangerous. It amazes me that it is turned on by default.


(Edit: I have been watching this thread in the hope that somebody had a more elegant method. When nobody did I thought that this clumsy approach would be better than none for you)

---

### Post by Scabby_al on 2005-12-21
I'll give that a shot. I'll see if I can rename the folder and see if that works. I'll have to remember where the option is to turn that off.

---

### Post by Cathbard on 2005-12-22
It's in Control Centre > KDE Components > Session Manager

To rename the .kde folder type: **mv .kde kdeold** at the prompt whilst in your home directory. What you do with the kdeold folder is up to you.
Goodluck.

---

