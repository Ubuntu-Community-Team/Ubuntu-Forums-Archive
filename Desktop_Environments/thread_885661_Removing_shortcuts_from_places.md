---
title: "Removing shortcuts from places"
date: 2008-08-10
forum: Desktop Environments
---

### Post by terrordrone on 2008-08-10
Hi

How do i remove shortcuts from places ?

I dont want Music , Documents , Pictures etc in places..

if i nautilus > bookmarks > edit bookmarks > remove (all) , it comes back on rebooting..

how do i get rid of this?

thanks

---

### Post by terrordrone on 2008-08-11
bump...

---

### Post by Rhubarb on 2008-08-11
You need to edit this file: ~/.gtk-bookmarks

**Alt + F2**
Then enter in:
```
gedit ~/.gtk-bookmarks
```
There you may delete the items you do not wish to see in your Places menu.

---

### Post by terrordrone on 2008-08-11
> **Rhubarb said:**
> You need to edit this file: ~/.gtk-bookmarks

**Alt + F2**
Then enter in:
```
gedit ~/.gtk-bookmarks
```
There you may delete the items you do not wish to see in your Places menu.
tried it and its back on reboot :(

---

### Post by Rhubarb on 2008-08-12
Check to see if your ~/.gtk-bookmarks file still contains the places you deleted before.
If they come back, you could try and make the ~/.gtk-bookmarks file read-only.  This may solve it for you.

---

### Post by rated727 on 2008-08-13
_correction: this only works until rebooted. (I almost never shut it down)_ 


The following SIMPLE method worked for me.  

Open places - computer.  In the left panel you will find icons for the things that you want to eliminate from the list.  Right-click and select "remove"
 
They are removed from the left panel AND from the list when you click "Places"

Should you ever want to return them, (or add other folders to the list) open the folder that contains the icon - left-click-hold and drag it to the left panel.

---

### Post by terrordrone on 2008-08-13
> **rated727 said:**
> _correction: this only works until rebooted. (I almost never shut it down)_ 


The following SIMPLE method worked for me.  

Open places - computer.  In the left panel you will find icons for the things that you want to eliminate from the list.  Right-click and select "remove"
 
They are removed from the left panel AND from the list when you click "Places"

Should you ever want to return them, (or add other folders to the list) open the folder that contains the icon - left-click-hold and drag it to the left panel.
thats the first thing i tried and realised it was coming back after re-boot

---

### Post by DouglasAWh on 2010-05-28
It's been ~2 years.  Is there really no answer to this yet?

---

### Post by marmux on 2010-06-17
yes there is (at least) one. 
you can do it by selecting "Edit bookmarks" from the "Bookmarks" menu of any nautilus window.

[http://ubuntuforums.org/showpost.php?p=5393736&postcount=3]("http://ubuntuforums.org/showpost.php?p=5393736&postcount=3")

cheers,
   m

---

### Post by funonline41 on 2010-09-06
1) Open File Manager 
 
a) Click Places
b) Click on Home Folder
 
2) Notice the Places on the left side column
3) The bookmarks are at the bottom
4) Right Click and Remove the item - Easy

---

### Post by braikar on 2011-03-13
The solution is in /home/user/.config/user-dirs.dirs !

By default it looks something like:
```

XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOWNLOAD_DIR="$HOME/Download"
XDG_MUSIC_DIR="$HOME/Music"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PICTURES_DIR="$HOME/Pictures"

```

change it to:
```

XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"

```

And on the next reboot the bookmarks won't reappear.
But one tiny problem with that is that programs that by default use these folders declarations, might need to modified to point to the correct directory, but it's not really annoying to change..

If you notice a program for example that deals with videos and dumps all the videos in /home/user/ (because that's now where the video folder is defined), just go and change the location of that dir manually...

---

### Post by rowanimox on 2011-06-10
what about the one above the favorites? i was trying to mount an image and now i cant get rid of it...

---

### Post by braikar on 2011-09-26
rowanimox: gp check there [http://ubuntuforums.org/showthread.php?t=1701478](http://ubuntuforums.org/showthread.php?t=1701478)
in short mount the image somewhere else than in your home folder and use mount --bind on startup to link it to the folder in your home folder and it will disappear as a mounted volume.

---

