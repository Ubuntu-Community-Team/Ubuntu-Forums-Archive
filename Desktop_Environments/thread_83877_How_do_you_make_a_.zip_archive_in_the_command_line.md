---
title: "How do you make a .zip archive in the command line?"
date: 2005-10-29
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-10-29
I am in a Half Life clan and I need to zip up my custom sprites I make for the teammates so I can include the original .bmp file, the .spr file, and the readme.

I'm the only person in my clan who uses linux, so I don't want to make people download extra programs to use .tar.gz or .tar.bz2 archives.  I use the Sprite Suite through WINE and Steam through Cedega, and since Half Life 1 is fairly old I see no performance dips and it doesn't interfere with my clan at all :D

I just need to get these files zipped up.  Thanks to anyone who helps me!

---

### Post by Xian on 2005-10-29
I would encourage you to read man zip for more info.

```
$ man zip
```

Having said that, here is the basic command:

```
$ cd /path/to/directory/
$ zip -r name_of_file.zip files
```

To unzip the file in Linux:

```
$ unzip filename.zip
```

---

### Post by DoeRayMe on 2005-10-29
Yes ^, Or right click the folder, choose Create Archive, then type your extention in

More simple

---

### Post by bryan986 on 2005-10-29
I would encourage them to get a new program like izarc or 7zip that can support all those formats...

---

### Post by Xian on 2005-10-29
[QUOTE=DoeRayMe]Yes ^, Or right click the folder, choose Create Archive, then type your extention in

More simple[/QUOTE]
That is a good method, but you lose control of a multitude of options that you may need or find to be useful. But hey, whatever works for you is all you should want. 

I like the idea of getting your pals to adapt. :)

---

