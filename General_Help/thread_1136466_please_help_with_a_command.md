---
title: "please help with a command"
date: 2009-04-25
forum: General Help
---

### Post by lordgafal on 2009-04-25
hi 

i have a hard drive filled with music (500g of it )

but theres tons of pictures text info m3u files i wanna get rid of but going true the folders manually would take me forever 

so im shure theres a way to clean this in 1 command probably with rm

can someone tell me the exaxt command to remove all in the hard drive (inclueding subfolders)

.txt
.jpg
.JPG
.gif
.GIF
.TXT
.nfo
.NFO
.m3u
.M3U

in /media/zic

thank a lot

---

### Post by _Purple_ on 2009-04-25
The following command will remove all the files of .txt format. 
```
rm /media/zic/*.txt
```

This will remove all the files of .txt format from the directory zic. To remove other files, replace .txt by that format. To remove the .txt files from all the subdirectories too, you can use
```
rm -rf /media/zic/*.txt
```
Be careful while using this command as a single typo can erase your hdd.

---

### Post by lordgafal on 2009-04-25
thank a lot man

ill do it with ls instead of rm before to make shure

---

### Post by lordgafal on 2009-04-25
uberbob@uberbob-server:/media/zic/my music$ ls -rf *.txt
ls: cannot access *.txt: No such file or directory

mmmm yet i know there is some 

uberbob@uberbob-server:/media/zic/my music$ ls -rf *.mp3
ls: cannot access *.mp3: No such file or directory
mmmm theres over 90k of em how come it cant find them

---

### Post by _Purple_ on 2009-04-25
If you are trying to list all the files of certain type, e.g. .txt, you can use the following command
```
find -name "*.txt"
```

---

### Post by maheshasolkar on 2009-04-25
> **_Purple_ said:**
> If you are trying to list all the files of certain type, e.g. .txt, you can use the following command
```
find -name "*.txt"
```

And when you are sure you are finding the right files, remove them like so:

```
  find -name "*.txt" | xargs rm -f
```

---

### Post by sahabcse on 2009-04-25
sudo rm -rf *.txt*

---

### Post by jwbrase on 2009-04-25
> **sahabcse said:**
> sudo rm -rf *.txt*

But be sure that you've switched to the directory first! You could end up wiping out txt files in places you don't want to if you're in the wrong directory.

```
cd /media/zic
```

And to be sure you're in the right directory:

```
pwd
```

Which should return /media/zic

---

