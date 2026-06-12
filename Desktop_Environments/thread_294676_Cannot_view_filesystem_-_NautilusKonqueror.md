---
title: "Cannot view filesystem - Nautilus/Konqueror"
date: 2006-11-07
forum: Desktop Environments
---

### Post by Genican1 on 2006-11-07
I recently upgraded to Edgy, and have noticed that the filesystem is no longer availiable for viewing in Nautilus or Konqueror.  I can view the "Home" and "Media" but not "bin", "root", or anything else.  Even when I "gksudo nautilus", these folders are not viewable.  I have no problem viewing them with Thunar, or even firefox (file:///), but Nautilus and Konqueror won't let me.  Any ideas?

---

### Post by Jucato on 2006-11-07
> **Genican1 said:**
> I recently upgraded to Edgy, and have noticed that the filesystem is no longer availiable for viewing in Nautilus or Konqueror.  I can view the "Home" and "Media" but not "bin", "root", or anything else.  Even when I "gksudo nautilus", these folders are not viewable.  I have no problem viewing them with Thunar, or even firefox (file:///), but Nautilus and Konqueror won't let me.  Any ideas?

I'm presuming you are using Kubuntu? You might want to take a peek at this page: 

[https://wiki.kubuntu.org/KubuntuHiddenFiles](https://wiki.kubuntu.org/KubuntuHiddenFiles)

---

### Post by joebrandt on 2006-11-10
The root directory contains a file called /.hidden. Open this in a text editor and delete the names of the directories which you want to have shown.

Deleting the /.hidden link is not a permanent solution, as it will be restored during the next update of the kubuntu-desktop-setting package.

---

### Post by msak007 on 2006-11-21
Thanks for the links. Now that I know the solution it's a pretty easy fix, but annoying nonetheless. The wiki should be updated to say that you can simply comment the directory names out though instead of deleting them. This makes for easy reversal if you decide to hide them again.

---

