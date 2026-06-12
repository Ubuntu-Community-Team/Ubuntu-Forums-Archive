---
title: "File appeared to delete, but didn't!"
date: 2006-06-22
forum: Desktop Environments
---

### Post by alyson on 2006-06-22
I'm probably just overlooking something, but I attempted to delete a large file (around 4 GB) by right-clicking on it, then selecting "Move to Trash."  This made the file disappear--albeit without actually going into the trash can (perhaps the trash can can handle only so much?)--but when I check my free hard disk space, it looks as if the file is still there, hiding somewhere.  I tried running a search for the file, but it yielded no results.  Somewhat ironically, I added 5 GB more to my Ubuntu partition just a few hours before; now I've pretty much lost that 5 GB!

What's going on here?  I probably just did something weird, but I'd like to have those extra 4 GB.

---

### Post by vigleik on 2006-06-22
How did you check your disk space? "du" gives you a detailed list, "df -h" gives you an overview over each partition. You can install a neat little program called filelight (with apt-get) which gives you a graphical view of what's taking up the space. If you're looking for the file in a file browser (nautilus/konqueror), be sure to enable viewing hidden files. "ls -l -a" from the command line should give you a list, including hidden files and file sizes.

If everything else fails, and it just doesn't add up, restart. Even though that's not supposed to be necessary in linux it sometimes helps. By the way, just in case you're confused about where the trash actually is, it's not in $HOME/.Trash/, but in $Home/.local/share/Trash/.

Vigleik

---

### Post by alyson on 2006-06-23
Thanks for the help!  And thanks for introducing me to Filelight; it's a really neat program.  I eventually found the file by browsing my files in Nautilus as root.  It was located in a hidden .Trash directory in /root/.  I thought I'd already checked there, but apparently in my frustration I forgot or overlooked it.  In any case, I'm glad I have 4 more gigabytes of free space, even if I do feel sort of silly for not being able to figure that one out on my own.

---

