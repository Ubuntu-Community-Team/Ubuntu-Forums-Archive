---
title: "GNOME Panels - They Hate Me"
date: 2009-11-05
forum: Desktop Environments
---

### Post by JasonInferno on 2009-11-05
Alright, my GNOME panels, after reboot, have decided to clear themselves off, and now I have no way to restore some of the original icons and items - they'renot found in the panel menu.
 
A fresh install is out of the question, as I have no way to backup files. My internet is also shot due to this panel messup. An internet-based solution is also out of the question.

---

### Post by realzippy on 2009-11-05
No way by right-clicking on panel and readding notification-area,main-menue and other stuff?

---

### Post by pastalavista on 2009-11-05
You can re-install Ubuntu without re-formatting the drive. Just do the install process again making sure you use the MANUAL mode. When the partitioner appears don't change anything except UNCHECK all the 'format' boxes and click 'install'. Your data won't be touched but all your config files will be overwritten and you'll need to run the updates again.

---

### Post by kixome on 2009-11-05
you can also use 8.04, or 9.04 and have not nearly as many bugs

---

### Post by JasonInferno on 2009-11-05
> **kixome said:**
> you can also use 8.04, or 9.04 and have not nearly as many bugs
 
FUN FACT: I run 9.04

---

### Post by JasonInferno on 2009-11-05
> **pastalavista said:**
> You can re-install Ubuntu without re-formatting the drive. Just do the install process again making sure you use the MANUAL mode. When the partitioner appears don't change anything except UNCHECK all the 'format' boxes and click 'install'. Your data won't be touched but all your config files will be overwritten and you'll need to run the updates again.
 
Would I use the CD image, the text-based installer, or Wubi? If I'm to use Wubi, then forget it - Windows doesn't work on my machine anymore

---

### Post by pastalavista on 2009-11-05
> **JasonInferno said:**
> Would I use the CD image, the text-based installer, or Wubi? IF I'm to use Wubi, then forget it - Windows doesn't work on my machine now.
I did it a few times with the live CD but have no experience with the text installer. I imagine you could use it too, but I don't know how. 

I've been Windows-free since 7.10 so I know nothing about Wubi except what I've read. 

An easy way to re-install all your packages after you re-install Ubuntu is to use Synaptic Package Manager and, under the file menu, "Generate a package download script". Save it somewhere else* and run it after the re-install. Also, you should save a copy of /etc/apt/sources.list... *in a different directory so it won't be overwritten.

---

### Post by JasonInferno on 2009-11-05
Thanks. I'm not too worried 'bout my software, just my documents.
I'll get my old LiveCD.

Thanks again, Pasta!

---

