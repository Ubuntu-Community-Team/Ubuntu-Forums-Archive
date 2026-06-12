---
title: "Linking folders to user directory"
date: 2008-11-29
forum: Desktop Environments
---

### Post by bdelin88 on 2008-11-29
Ok, I am new to Ubuntu and really trying to figure this thing out... here's what I'd like to do.

I have the user folder, my user folder, with Music and Video folders, etc, blah blah blah.

In window$ I always had a windows partition and I kept all of my sensitive data on a separate partition and what I did was I linked all my music and video folders over to that partition, so obviously when I clicked music, it represented the music folder but was actually stored on a different partition, for example, "E:\" when windows partition was located on "C:\".

Is there some sort of way to do this in ubuntu via the command line?  I don't think it is possible to mount a folder inside of a folder, but I would like to click my "Music" folder in my home directory and have it take me to my music folder on sdb1.  

Any ideas?

---

### Post by stella2657 on 2008-11-30
> **bdelin88 said:**
> Ok, I am new to Ubuntu and really trying to figure this thing out... here's what I'd like to do.

I have the user folder, my user folder, with Music and Video folders, etc, blah blah blah.

In window$ I always had a windows partition and I kept all of my sensitive data on a separate partition and what I did was I linked all my music and video folders over to that partition, so obviously when I clicked music, it represented the music folder but was actually stored on a different partition, for example, "E:\" when windows partition was located on "C:\".

Is there some sort of way to do this in ubuntu via the command line?  I don't think it is possible to mount a folder inside of a folder, but I would like to click my "Music" folder in my home directory and have it take me to my music folder on sdb1.  

Any ideas?
hi, i do the same thing,main menu,places - use bookmarks, you can make as many links to sub folders or indervidual files as U like.

---

### Post by cammin on 2008-11-30
You can mount a directory to another directory, with the **bind** option.

But, for what you want to do, you should use a symbolic link.
**ln -s /from/here /to/here**

---

