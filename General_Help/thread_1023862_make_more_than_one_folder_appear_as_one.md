---
title: "make more than one folder appear as one"
date: 2008-12-28
forum: General Help
---

### Post by nephish on 2008-12-28
Hey all, 
i have a few hard drive partitions in 3 drives that I want to share.
Is there an applicaiton that will cause these to all appear as a single folder? 

i mean i have 
/mybox/stuff  which is /dev/sdb1
/mybox/stuff2 which is /dev/sdb2
/mybox/stuff3 which is /dev/sda2

and so on, 
is there a way to have them all appear as just /mybox/stuff ?
or something similar?

thanks

---

### Post by skullmunky on 2008-12-28
I don't think you can.  The problem is this: 

If you wanted to just display the contents of all three directories together, that'd be no problem.  So, say you have a folder configured this way, you open it, you see what's inside all three of your directories.  But let's say you now copy another file into that folder.  Which one of the three does it go into?

---

### Post by nephish on 2008-12-28
all i need to do is display the results as one folder. Only one computer needs write access, mine. Basically, i am running one box as a file server, and i need it to look like only one folder. I can put the files where i need them based on size, etc.  
thanks

---

### Post by ajcham on 2008-12-28
You could create a new folder and fill it with symlinks to the files on each of your drives.

A short script could automate the process, and you could get this to run periodically to take into account newly created files.

For the reason stated in skullmunky's post, you would still need to enter the proper directory to save or copy new files into stuff, stuff1 or stuff2. But for the purpose of merely accessing existing files, I think my suggestion would be OK.

---

### Post by steeleyuk on 2008-12-28
From what I've read, Unionfs can do something like this.

[http://www.linuxjournal.com/article/7714](http://www.linuxjournal.com/article/7714)

Though I've had a quick play and not managed to get it working yet.

---

### Post by ajcham on 2008-12-28
[QUOTE=me]You could create a new folder and fill it with symlinks to the files on each of your drives.

A short script could automate the process&#8230;[/QUOTE]

OK, looks like it was easier than I realised.

First, create the directory you want to hold everything. In my example script it is /mybox/mystuff.
```
mkdir /mybox/mystuff
```
Then you can use the following script:
```
#!/bin/bash

#Empty mystuff folder in preparation to prevent dead links
rm -rf /mybox/mystuff/*

#Create symlinks
ln -s /mybox/stuff/* /mybox/mystuff/
ln -s /mybox/stuff1/* /mybox/mystuff/
ln -s /mybox/stuff2/* /mybox/mystuff/

```

The mystuff folder will now appear to hold all the contents of the other three stuff folders, as at the time the script was run. Of course, any changes to the contents of the folders will not be reflected in *mystuff*, eg. new files will not be seen and deleted files will still have links to them, so it will be necessary to rerun the script periodically.

EDIT: Additional point - if you have identically named files or folders in the root of your stuff directories, a symlink will only be created for the first one. You would need to edit the script a bit to compensate for this.

---

### Post by nephish on 2008-12-28
great tips guys, thanks
will look into unionfs, if it comes easy, i will use that,
otherwise the directory full of links looks good because it solves another couple of problems too.

---

