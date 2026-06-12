---
title: "Feature request for copying files"
date: 2009-05-21
forum: Desktop Environments
---

### Post by mercury80 on 2009-05-21
Don't know if I post this in the correct category, but here it goes...
I copy a lot of large files to and from portable devices, often from different places to one spot. (I love the "List View" in the file browser so I can expand folders and pick files from different folders to copy them into one folder) I don't like to copy several big files at the same time, because it seems slow and messy. I don't want my files all fragmented. So I would like the different "File Operation's" to cue as if I was was draging all the files into the respective folder in one "move". Don't know if I was able to make my self clear, but I'll be happy to clarify.

---

### Post by skullmunky on 2009-05-21
are you creating something like a mirror copy, with the same directory structure in the source and the destination?  

the usual way to do that is with the "rsync" command, which synchronizes two directories (including subdirectories, and also over the network).

I just discovered this neat thing in Dolphin on KDE 4.2.2 which I've never seen before, which might be helpful to you.  Say you have a folder on your hard drive and one with the same name on your portable, like "Music".  Traditionally, dragging "Music" to your portable overwrites everything, which is tedious if you have many GB of files and only one or two new files.  

Dolphin will ask you if you want to "Write Into" the folder, which means it will not overwrite the directory, but copy files into it.  if there are duplicates, like your other 60 GB of music which is already on both drives, you can tell it to skip them, so it only copies the new ones.  Neat!

---

### Post by mercury80 on 2009-05-21
no. not a mirror. when i keep the directory structure it is easier...
but when i copy several things from several sources to one device i don't want all the processes simultaneously. i want all the files to copy sequentially. make it cue up, and wait for it's turn... so the files don't get all fragmented... 

but i will have use for the "rsync" command aswell. tnx...
is "write into" available in ubuntu aswell?

---

