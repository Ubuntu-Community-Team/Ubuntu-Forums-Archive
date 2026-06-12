---
title: ".png bug in gallery"
date: 2005-11-04
forum: Forum Feedback &amp; Help
---

### Post by Freddy on 2005-11-04
I know I have reported this before but I believe that this bug really need some sort of fix. 

When you upload a .png file to one of the galleries, it get scaled down to a thumb and to a "middle" resolution, both of the scaled down pictures get distorted (if you want a example browse to [www.ubuntuforums.org/gallery/showimage.php?i=1234&c=2)](www.ubuntuforums.org/gallery/showimage.php?i=1234&c=2)).

This isn't happening with a uploaded .jpg but as this is a debian based distro with a open source and format? thinking, it feels kind of weird that you have to use a property fileformat for a full compatibiltie with the gallery. 

Anyways thanks for a wonderful forum and grat changes in the last couple of months.   /// Freddan

---

### Post by ubuntu-geek on 2005-11-08
Yes, I think its the way gd2 resizes the image. However since its just the thumbnail image I wouldnt worry if you click on it it will show the original.

---

### Post by Freddy on 2005-11-08
[QUOTE=ubuntu-geek]Yes, I think its the way gd2 resizes the image. However since its just the thumbnail image I wouldnt worry if you click on it it will show the original.[/QUOTE]
It doesn't show the "original" when the thumbnail is clicked, it will show another scaled and distorted (around) 640x480 picture, when that is clicked the orginal shows, if it only were the thumbnail that was messed, I wouldn't worry about it. I don't know why this bug isn't happening with .jpg. This is the only forum I've noticed this way of handling .png files.   /// Freddan

---

### Post by ubuntu-geek on 2005-11-08
ok i'll hit up the developers of that addon..

---

### Post by Freddy on 2005-11-08
Thanks. 
Somehow this bug has grown on my nervs, don't know why it just has :).   /// Freddan

---

