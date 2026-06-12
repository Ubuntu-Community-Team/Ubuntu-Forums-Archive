---
title: "DosBox"
date: 2008-08-12
forum: Gaming &amp; Leisure
---

### Post by Sunfist on 2008-08-12
Anybody using DosBox under linux. I could use some help getting my game directory mounted. Under windows its on E:\MSDOS\mygames. Under linux it appears to me as being media\MSDOS\mygames but when I try to mount that it says that directory doesnt exist. I assume its because I am not telling it that its on the E: drive, whats the linux way of saying E:...is it one of those hd3 things?

---

### Post by grossaffe on 2008-08-12
> **Sunfist said:**
> Anybody using DosBox under linux. I could use some help getting my game directory mounted. Under windows its on E:\MSDOS\mygames. Under linux it appears to me as being media\MSDOS\mygames but when I try to mount that it says that directory doesnt exist. I assume its because I am not telling it that its on the E: drive, whats the linux way of saying E:...is it one of those hd3 things?

I'm not what you'd consider a linux expert but here's how I think you need to do this:

first, your HDD that contains the files you are attempting to access in dosbox is not mounted in linux yet.  what you *should* do (I'm pretty sure) is mount have the hard drive mounted in Linux, and then in DOSbox you can mount it from where it is mounted in linux (if that makes any sense to you).

---

### Post by FranMichaels on 2008-08-12
[QUOTE=Sunfist]Under linux it appears to me as being media\MSDOS\mygames[/QUOTE]

Linux, like addresses on the web, has / in that direction

So try /media/MSDOS/mygames

Other than that, you can just right click on the game or directory you want dosbox to mount (choose open with, then custom command, enter dosbox.) I prefer this method as I can just double click to launch games, and the mounted game won't see outside it's own directory (on the off chance I ever run into an old DOS virus... if those would even work on dosbox... but doesn't hurt to be safe. :D)

---

### Post by grossaffe on 2008-08-12
> **FranMichaels said:**
> Linux, like addresses on the web, has / in that direction

So try /media/MSDOS/mygames

Other than that, you can just right click on the game or directory you want dosbox to mount (choose open with, then custom command, enter dosbox.) I prefer this method as I can just double click to launch games, and the mounted game won't see outside it's own directory (on the off chance I ever run into an old DOS virus... if those would even work on dosbox... but doesn't hurt to be safe. :D)

heh, I wrote batch files to run all my DOS games.

by the way, is there a version of dosbox where the configuration commands actually work?  I find the only way to change configuration (such as full screen or mouse sensitivity) is to close dosbox and manually edit the config file every freaking time.  There are commands that *should* do it but they don't do a thing.

---

### Post by The Squig on 2008-08-13
think you ca mount it like this for example: mount c /home/user/folder/ 

Dont have dosbox on this pc so I cant test but on my other linx box it runs very well. If you still have problems tomorrow ill look it up.

Edit: Ok i shouldnt be posting at 6am. what was said earlier about the partiton not being mounted in linux sounds about right.

A very easy way to mount your nfs drives in ubuntu is to download ntfs-config from the repo.
its very easy to use.

---

### Post by Sunfist on 2008-08-13
Actually I have my E: drive formated for FAT16 so both windows and Linux can see/use it. But I'll try some of the ideas posted here tomarrow.

---

