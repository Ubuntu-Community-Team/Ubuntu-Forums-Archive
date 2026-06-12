---
title: "Searching for files and folders"
date: 2007-03-20
forum: Desktop Environments
---

### Post by Azyx on 2007-03-20
Hi.
How do I make a search for files on my computer.  I want to search more than one hdd or the file system. I also have a NTFS-disk with ntfs-3g drives. Want to find anything with a part of a word.

If i chose to search filesystem i dont find files on my ntfs disk. I have 3 disks so it's a lot of work to find for a file.

/azyx

---

### Post by kidders on 2007-03-20
Hi there,

Try **find /path -name "*word*"** or **find /path -iname "*word*"**, where "path" is where you want to start searching from and "word" is the filename fragment you want to search for.

**Edit:** The **find** process will probably make your system a bit sluggish. You can reduce the effect slightly with **nice** if you want.

---

### Post by taurus on 2007-03-20
Applications -> Accessories -> Terminal
```
sudo find / -name **filename** -print
```

---

### Post by nsleiman on 2007-03-20
if you have the disks mounted all under / you should be able to find the files i guess.

example:

(look for gdm as a word in the file rc.local)
grep "gdm" /etc/rc.local
 this will consider gdm as a pattern for search and not a string i guess

looking for specific files:
find / -name nsleiman.jpg

(seems many were faster :)

---

### Post by Azyx on 2007-03-20
I don't get any hit, on files that exist on my ntfs-volume.

azyx@computer:~$ sudo find / -name movie.avi -print 

And a respons in swedish, that says someting like (I have Ubuntu in swedish)

find: Warning: Number of hard links /proc/4802 are wrong: This may be a bugg in drivers for the filesystem. Turning automatic on find:s switch -noleaf. Earlier results may have failed to include folders that would have being searched.
find: /proc/6178/task: file or folder does not exist
find: /proc/6178/fd: file or folder does not exist
find: /proc/12818/task: file or folder does not exist
find: /proc/12818/fd: file or folder does not exist

Could it be because I use NTFS and ntfs-3g on one hdd? I have 3 hdd i the system, ut only one ntfs.

/azyx

/Azyx

---

### Post by taurus on 2007-03-20
Is the file you are looking for called **movie.avi**?

```
sudo find / -name [COLOR="Red"]*.avi[/COLOR] -print
```

---

### Post by Azyx on 2007-03-20
no, it was an example, it was a longer name that exist on the disk.


> **taurus said:**
> Is the file you are looking for called **movie.avi**?

```
sudo find / -name [COLOR="Red"]*.avi[/COLOR] -print
```

---

### Post by Repabil on 2007-03-20
If you're using gnome you can also search by:
[list][*]Places -> Search for files...
[*]Open the folder you want to search for in [Nautilus](http://www.gnome.org/projects/nautilus/) and choose Go -> Search or hit Ctrl-F.[/list]

---

