---
title: "reaming files"
date: 2009-02-26
forum: General Help
---

### Post by mohxinn on 2009-02-26
I have just ported to ubuntu and I am loving it :)

As i have just ported so I have a lot files with space in the filenames. I wanted to know if there is an easy way (via the terminal) to replace spaces with dashes in filenames so that I can access them easily using the terminal?

Thanks

---

### Post by mohxinn on 2009-02-26
I got my answer for filenames:

[http://ubuntuforums.org/showthread.php?t=959109&highlight=rename+space](http://ubuntuforums.org/showthread.php?t=959109&highlight=rename+space)

What about directory names? Is there a similar command?

---

### Post by mb_webguy on 2009-02-26
You can specify filenames with spaces in the terminal by either double-quoting them (i.e. gedit "my text file.txt"), or by escaping the spaces with a backslash (i.e. gedit my\ text\ file.txt).  The terminal will do this automatically if you start typing the filename and hit the tab button.

---

### Post by SuperSonic4 on 2009-02-26
```
mv my\ file my_file
```

mv is move, it's moving the old file to the new one. Remember to use -R for recursive

---

### Post by cariboo on 2009-02-26
I use this for removing the spaces from mp3 file names:

```
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done
``` 

I got it from this [howto]("http://tldp.org/HOWTO/MP3-CD-Burning/index.html")

Jim

---

### Post by kaibob on 2009-02-26
> **mohxinn said:**
> ...What about directory names? Is there a similar command?

The rename command in the thread you reference renames both files and directories in the current directory:

```
rename -n 's/ /_/g' *
```

The -n option does a dry-run. Substitute -v for -n to actually make the changes.

---

### Post by 0bso on 2009-02-26
Instead of renaming all your files why not just use \ or ' to handle the spaces?

For example to go to /home/user/vacation photos/ in ther terminal you would type:
cd /home/user/vacation\ photos 

Or you can put the path in 's and leave the space as normal:
cd '/home/user/vacation photos' 


Using either rather than renaming stuff will save you a lot of headache.

---

