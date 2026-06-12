---
title: "Changing file directory"
date: 2009-12-05
forum: Desktop Environments
---

### Post by romber on 2009-12-05
Hi, I am new to the Linux community and am loving it so far. Anyways, my question is fairly simple regarding file paths. I have tried to search for the answer, but I don't believe I am writing it clearly so I am going to have to explain what I am trying to do.

I want my files that are preset as Downloads, Documents, Pictures etc. (mainly the files you see in the quick browser next to the start menu in kubuntu) to open up a location of my preference instead of the default location they open up to.  I checked in properties for individual files to see if I could change the file path, but nothing really stood out as a way to do so.

So, if anyone could inform me on how to change the file path of my folders, I would greatly appreciate it.

Thanks!

---

### Post by benerivo on 2009-12-05
I would do it with```
ln -s '/mnt/Storage/My Downloads' ~/Downloads
```where the first part is my existing target folder (that i want the preset folders to use) and the second part is a folder that will be created in my home directory (so if you've already got a Downloads folder then delete it first).

---

### Post by akashiraffee on 2009-12-05
That's what I would do too, it's simple and it guarantees that any software that uses these folders will still work without you having to modify configuration for all of them, etc.

'ln -s'  creates a "symbolic link", or for short, "softlink" or "symlink" (this is contrasted with a "hard link" which is much less common in practice).  They are quite similar to windows "shortcuts" but perhaps more versatile.

[http://kb.iu.edu/data/abbe.html](http://kb.iu.edu/data/abbe.html)
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

Notice, you could link all of ~/Documents, ~/Photos, ~/Music, etc, to one single directory if you want ("MyStuff" or whatever).  There is no limit to the number of softlinks to a file or directory that can exist.

You will have to transfer the existing contents of the directories first and then erase them (make sure your symlink has EXACTLY the same name as the directory you erase, and is in the same place).

---

### Post by peepingtom on 2009-12-05
I just answered this question HERE:[http://ubuntuforums.org/showthread.php?t=1346849](http://ubuntuforums.org/showthread.php?t=1346849)
He asked 2 hours after you :D

he is using gnome but I think that sol'n will work for you.

---

### Post by bailout on 2009-12-05
Open System Settings, click on About Me, then Paths

---

