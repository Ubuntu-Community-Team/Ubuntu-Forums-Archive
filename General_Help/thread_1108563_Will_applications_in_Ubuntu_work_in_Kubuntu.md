---
title: "Will applications in Ubuntu work in Kubuntu?"
date: 2009-03-27
forum: General Help
---

### Post by goettlek on 2009-03-27
So I've been using Ubuntu Studio but have been thinking about migrating over to Kubuntu. However I really like some of the applications that are in Ubuntu Studio, like Hydrogen and MuSE. Will the appllications from Ubuntu Studio work in Kubuntu?

Sorry if this seems like a silly question but I'm just getting started in Linux. Thanks!

---

### Post by SuperSonic4 on 2009-03-27
Yes, they should although you'll need additional libraries

---

### Post by loomsen on 2009-03-27
You can have different desktop managers installed. GDM for instance offers a menu to select your session before you login, like KDE, gnome, xfce.... 

Ubuntustudio should work as well, tho I don't have it, so I can't tell you for sure. Just grab the kubuntu-desktop metapackage and see what happens.

---

### Post by goettlek on 2009-03-27
> **SuperSonic4 said:**
> Yes, they should although you'll need additional libraries

Will it prompt me for those libraries if I'm missing them, or somehow let me know which libraries I need to get?

@loomsen: I think I'll try that, but part of why I'm thinking about switching is for hardware compatibility since in Kubuntu all my hardware works and in Ubuntu Studio I'm running into troubles.

---

### Post by mb_webguy on 2009-03-27
Remember that Linux is the operating system.  The desktop environments are just programs that run on Linux.  However, there are different graphic libraries.  Gnome (used by Ubuntu) uses the GTK+ library, and KDE (used by Kubuntu) uses the Qt library.  Programs written using the GTK+ library will therefore integrate better with Gnome, and programs written using the Qt library will integrate better with KDE.  

As long as you have the appropriate library installed, however, the program will run.  And since the libraries are dependencies for the program, if you don't already have them they will be installed automatically when you install the program.

---

### Post by goettlek on 2009-03-27
> **mb_webguy said:**
> Remember that Linux is the operating system.  The desktop environments are just programs that run on Linux.  However, there are different graphic libraries.  Gnome (used by Ubuntu) uses the GTK+ library, and KDE (used by Kubuntu) uses the Qt library.  Programs written using the GTK+ library will therefore integrate better with Gnome, and programs written using the Qt library will integrate better with KDE.  

As long as you have the appropriate library installed, however, the program will run.  And since the libraries are dependencies for the program, if you don't already have them they will be installed automatically when you install the program.

Thanks for a great answer! That makes a lot of sense! Looks like I'll probably switch over then. Thanks a lot for all your guys great answer.

---

### Post by jacksaff on 2009-03-27
Well there's no need to switch over. "sudo apt-get install kubuntu-desktop" will add kde to your system. Log out and select kde as the session type and log back in and you will be in kde. 

Because you already have all of the applications you need and their dependencies, they will all still work (though they might look slightly different under kde). Get tired of kde and you can log back out and re-select gnome as your session type.

---

### Post by goettlek on 2009-03-28
> **jacksaff said:**
> Well there's no need to switch over. "sudo apt-get install kubuntu-desktop" will add kde to your system. Log out and select kde as the session type and log back in and you will be in kde. 

Because you already have all of the applications you need and their dependencies, they will all still work (though they might look slightly different under kde). Get tired of kde and you can log back out and re-select gnome as your session type.

My problem with Ubuntu Studio has been hardware compatibility. Wireless, audio ins and outs, etc. hasn't been recognized. I've tried lots of things and am pretty new to Linux. Kubuntu on the other hand already works with all my hardware just fine, so for now I'll just put on Kubuntu.

As far as packages go, I found this [http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/) so I can just get the packages quite simply I think. Thanks for the good idea though.

---

