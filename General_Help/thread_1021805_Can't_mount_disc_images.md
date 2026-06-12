---
title: "Can't mount disc images"
date: 2008-12-25
forum: General Help
---

### Post by ifflejink on 2008-12-25
So, I just downloaded gmountiso so that I could have a utility with a gui to mount .iso files, but whenever I try to mount an image, gmount-iso just says that loop0 is mounted on cdrom0. This happens with every disc image I've tried. Anyone have any idea what's going on? Thanks!

---

### Post by redsoxreed on 2008-12-25
Try right clicking on the .iso's and select "open with archive mounter" (or something like that, I'm not in front of my computer.)

EDIT: oops, I didn't realize you had xubuntu.  (the above only work if you have the gnome archive manager installed.)

---

### Post by iponeverything on 2008-12-26
you can mount it from the terminal.

```

mkdir disk
sudo mount -o loop1 <yourisoimage>.iso disk

```

---

### Post by ifflejink on 2008-12-26
Would I just do that in my normal terminal, not in a specific folder?

Also, I have a new problem. I can't unmount my old fuseiso images. When I try to do so using fusermount, I get the following output:
```
gavin@gavin-laptop:~$ fusermount -u /media/fuseiso
fusermount: entry for /media/fuseiso not found in /etc/mtab

```

However, I check /etc/mtab, and there definitely is an entry for /media/fuseiso. This problem is more significant, as I am simply losing this disk space. Any help here?

---

### Post by iponeverything on 2008-12-26
I am in the habit of doing everything from ~.  Just give it the path to the iso.

---

### Post by ifflejink on 2008-12-26
What command would I type in to do that?

Nevermind- I thought you were referring to something else. That one did work out.

---

### Post by glaxo357 on 2009-05-18
> 
glax@laptop:~/Games/Grim$ mkdir disk
glax@laptop:~/Games/Grim$ sudo mount -o gfd1.iso disk
[sudo] password for glax: 
mount: can't find disk in /etc/fstab or /etc/mtab
glax@laptop:~/Games/Grim$ 
 

Any ideas?

---

### Post by Legace on 2009-05-18
Do

```
sudo mkdir /media/iso
sudo mount -o ~/Games/Grimgfd1.iso /media/iso
```

---

### Post by charkoal on 2009-05-20
I tried that but i get a message coiming up with heaps of writing and then i try one of the options and it says cant find "*****" in /etc/fstab or /etc/mtab

---

