---
title: "Formatting and accessing my second HD"
date: 2006-03-06
forum: Desktop Environments
---

### Post by ubuntukid on 2006-03-06
I have two HD-drives on my computer. One with aprox 10 GB and the other with approx 50 GB. I installed Ubuntu on my 10 GB drive. I have an installation of SUSE on my second hd but I now wish to reformat it and use it as a second hd for storing media files like photos, movies, etc. At the moment though I can`t see it in my file system. I found a partitioning application which had an "enable" button.

Now I don`t want to do anything wrong so I`m asking here first as I`m still a newbie at this. How do I reformat my second HD for use as a storage device? It contains a Swap Partition and a partition called Partition 2.

---

### Post by Ramses de Norre on 2006-03-06
Install gparted (just apt-get it) and unmount the partitions you want to change.
All the options are quite obvious then, but you can ask for something specific when you've got something you don't understand.

---

### Post by ubuntukid on 2006-03-06
What is the Linux swap disk? It`s taking up 777 mb on my second HD. Is it needed?

---

### Post by Ramses de Norre on 2006-03-06
Do you have swap on your first hd too? Swap space is hard disk space that the os can use as ram. It only does this when it's running out of ram because it's a lot slower.
If and how much swap you'll want to have depends on how much ram you've got and how intensively you use your machine.

---

### Post by ubuntukid on 2006-03-06
Yes I do have a swap disk on my first HD. The same one that is used for my Ubuntu install. The reason I also have one on the second HD is because I have a copy of SUSE on it but I much prefer Ubuntu and wish to get rid of it.

If I have some swap disk on my second hd as well as my first will it utilize both or will it just ignore the second?

---

### Post by ubuntukid on 2006-03-06
I need to choose an access path. What is that?

---

### Post by Ramses de Norre on 2006-03-06
You made one partition of the hd? I guess the acces path would be the mount point, but is strange gparted asks that. I doesn't when I make a partition..
When does it asks? And what type of partition are you making?

---

