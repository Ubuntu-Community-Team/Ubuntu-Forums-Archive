---
title: "hard drive icon on desktop"
date: 2011-01-27
forum: Desktop Environments
---

### Post by DelSol on 2011-01-27
hello,

i would like to know how i can put a shortcut from my hard drive (the internal one) one my gnome desktop (like in mac os x). if possible it would be nice if i also  could see the space / remaining space all the time.

i tried to create a shortcut from filesystem, but right click and send to desktop does not work. also pressing ctrl+shift and dragging the filesystem symbol to the desktop does not really work.

os is ubuntu 10.10

thanks in advance!

---

### Post by marin123 on 2011-01-27
hit alt+F2 and type gconf-editor, open it. then open apps and go to nautilus. open that, and click on folder desktop. you can now check boxes you want on your desktop (computer, home, mounted drives etc.).

as for available drive space you will have to use something else. maybe screenlets or something like that.

fyi, you can see available disk space in bottom of nautilus (file browser) if you didnt select anything.

---

### Post by Elfy on 2011-01-27
Absolutely no idea at all what any mac looks like but if you want the hardrive to show on your desktop mount it.

To do so permanently it needs to be added to fstab. [You can use a GUI to do so - pysdm]("http://ubuntuforums.org/showthread.php?t=872197") - make sure that it is mounting in /media and not /mnt and it will show as long as you have not turned off the show volumes on the desktop.

[You can also edit fstab manually if you so wish.]("https://help.ubuntu.com/community/Fstab")

To see the space I would think that you could use conky and set it up to just show drive information. [http://conky.sourceforge.net/](http://conky.sourceforge.net/) 

It's in the repos so you can install it from synaptic. 

There is a large thread in the cafe you might be able to get some ideas from - [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by coffeecat on 2011-01-27
> **DelSol said:**
> i would like to know how i can put a shortcut from my hard drive (the internal one) one my gnome desktop (like in mac os x). if possible it would be nice if i also  could see the space / remaining space all the time.

i tried to create a shortcut from filesystem, but right click and send to desktop does not work. also pressing ctrl+shift and dragging the filesystem symbol to the desktop does not really work.

The one in Mac OS is actually a pseudo-representation of the filesystem. Open a Finder window with the desktop icon and compare what you see with 'ls /' in a MacOS terminal to see what I mean. We don't do pseudo-representations in Linux-land! :p

Anyway, to get the desktop shortcut you want, right-click on the desktop and choose 'Create Launcher'. Under Name put whatever desktop label you want. Under command you need:

```
nautilus /
```OK that and you have the launcher you need but with a Nautilus icon. If you want a different icon, right-click on it > Properties. In the Properties window click on the icon image and navigate to where your preferred icon is.

---

### Post by DelSol on 2011-01-27
> **coffeecat said:**
> The one in Mac OS is actually a pseudo-representation of the filesystem. Open a Finder window with the desktop icon and compare what you see with 'ls /' in a MacOS terminal to see what I mean. We don't do pseudo-representations in Linux-land! :p

Anyway, to get the desktop shortcut you want, right-click on the desktop and choose 'Create Launcher'. Under Name put whatever desktop label you want. Under command you need:

```
nautilus /
```OK that and you have the launcher you need but with a Nautilus icon. If you want a different icon, right-click on it > Properties. In the Properties window click on the icon image and navigate to where your preferred icon is.

thanks! that is the perfect solution. :D

---

### Post by Quattroa430 on 2012-03-25
While not exactly what you are looking for (I was looking for the same thing) I did find an alternative method... Install Cairo dock and Get new applets. One of the applets is disk free which tells you exactly how much space is left.

---

### Post by howefield on 2012-03-25
Old thread closed.

---

