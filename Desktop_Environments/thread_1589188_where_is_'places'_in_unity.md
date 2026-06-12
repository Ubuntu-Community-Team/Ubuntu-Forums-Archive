---
title: "where is 'places' in unity"
date: 2010-10-06
forum: Desktop Environments
---

### Post by gtr@frii.com on 2010-10-06
Not sure if this is the right forum.  In any case, I installed 10.10rc netbook on an hp mini210-1010nr.  I'd like to be able to mount some nfs and cifs mounts from other systems. I've grown accustomed to clicking:
places->computer->mnt to find my nfs mount points.  For the life of me I can't find places from the unity desktop/menus.  I thought perhaps files would get me there, but it is anchored at ~ (i.e., /home/user) and I don't see any obvious way to look at /.

---

### Post by Apolyonn on 2010-10-14
I need to know the answer too, I'd like to access my files from the 10.04 desktop partition and my Windows 7.  I could access my Windows files from Ubuntu's Desktop versions - it showed up as a 138gb file system - but in Unity, there is no "Places", and the file system is not showing up anywhere.

Help, please

---

### Post by phufax on 2010-10-15
I had this problem too. Essentially you just need to get nautilus to run so you can then navigate the files in the standard way. Either

i) click on any of the files/folders in the favourites area of the unity files/folders tab. Now there should be a small folder icon in the top right, clicking on that will open the normal filebrowser to let you navigate more easily.

if the icon doesn't appear, or this doesn't work for whatever reason

ii) open a terminal (shortcut should be ctrl+alt+t) and type "nautilus"  (without the quotes) and press enter. This will start the usual ubuntu filebrowser and you can navigate to the filesystems.

For both cases I recommend changing the favourites on the left so that the filesystems you need often will appear in the unity files/favourites area. This is a bit of a roundabout way of fixing this so I imagine there must be a better way, or a fix for unity itself coming soon.

hope this helps

---

### Post by phufax on 2010-10-15
Or alternatively, just click on the deleted items tab. That should open the filebrowser much more easily. :)

---

### Post by cariboo on 2010-10-15
I just added the nautilus icon to the panel.

---

### Post by John.Hood on 2010-11-13
In File Manager under File, is "Connect to Server"
Fill in the info.  There you are.

---

