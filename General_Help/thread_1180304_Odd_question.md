---
title: "Odd question?"
date: 2009-06-06
forum: General Help
---

### Post by Snyper64 on 2009-06-06
Is it possible to get the filenames of files that got deleted? I accidentally deleted my desktop folder on my backup drive and need to get the files back. Most of the files are just anime episodes I haven't had time to watch so all i need is the file names so that i can re download them. I know that there are programs out there that can restore lost partitions but I only had about 5 or 6 gigs of files on my desktop and i don't want to go through the hassle of restoring a whole partition just for a few files.

Does anybody have any ideas on how to do this?

---

### Post by tgalati4 on 2009-06-06
sudo apt-get install testdisk
man photorec

Good luck!

---

### Post by michy99 on 2009-06-06
Try installing ext3grep and using the --dump-names option. ```
ext3grep /dev/sdaX --dump-names > names.txt
```The drive should be unmounted. Use the actual device designation where I have /dev/sdaX. The output will be saved in names.txt (or whatever name you wish. Note: this can take a long time. Like several hours.

---

### Post by Snyper64 on 2009-06-06
Michy99, is there any way to recover just certain files? My girlfriend had 5 files on my machine that need restored. As for the rest i can download them again.

---

### Post by michy99 on 2009-06-06
If you know the name and path of the file then you can use ```
ext3grep /dev/sdaX --restore-file path/to/file
```This command should be run from the directory you want to save the recovered file to. Not from the partition you are recovering from. In fact, The partition you are recovering from should be unmounted. Replace /dev/sdaX with the device you are recovering from. Replace path/to/file with the path to the file you want to recover. Note that it does not start with a / for example to recover a file named test.rar located in the folder 'dogs' on /dev/sdb3 you would enter```
ext3grep /dev/sdb3 --restore-file dogs/test.txt
```

If you don't know the paths of the files you have to do the --dump-names option first as described above.

---

### Post by blueridgedog on 2009-06-06
I suggest you look at foremost as well.

[http://linux.die.net/man/1/foremost](http://linux.die.net/man/1/foremost)

---

### Post by Snyper64 on 2009-06-07
Thanks Michy99, I got back her files and am now halfway done re-downloading my lost files.

---

