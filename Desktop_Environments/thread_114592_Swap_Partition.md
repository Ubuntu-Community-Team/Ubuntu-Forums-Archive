---
title: "Swap Partition"
date: 2006-01-08
forum: Desktop Environments
---

### Post by tatacalu on 2006-01-08
hi !

when i installed ubuntu, i didn't have a swap partition.
today I made one, and I am not shure if ubuntu uses it.... dumps data on it. How can I make shure ?

Thank You!

---

### Post by soulestream on 2006-01-08
make sure its formatted for swap
make sure its in /etc/fstab

swapon -a


soule

---

### Post by tatacalu on 2006-01-08
Disk Manager says that is in /dev/hda6 and i can't change that, it isn't written in a text box, is more like a label.

---

### Post by dueY on 2006-01-08
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda3       none            swap    sw              0       0
```

Is my swap properly set up?  I've never edited anything to do with it.

---

### Post by towsonu2003 on 2006-01-08
```
free -m
``` will give you info on your memory usage, thus whether your swap is there... output will be in megabytes... you may see that too much memory is being used, that's okay. 

PS. DueY's fstab is fine for his.her own system.

---

### Post by tatacalu on 2006-01-08
```
root@ubuntu:~# free -m
             total       used       free     shared    buffers     cached
Mem:           503        466         37          0         23        236
-/+ buffers/cache:        206        297
Swap:            0          0          0

```

hmmm..... no swap used.
what can I do ?

---

### Post by Horndog on 2006-01-09
[QUOTE=tatacalu]```
root@ubuntu:~# free -m
             total       used       free     shared    buffers     cached
Mem:           503        466         37          0         23        236
-/+ buffers/cache:        206        297
Swap:            0          0          0

```

hmmm..... no swap used.
what can I do ?[/QUOTE]

Here is mine:
```

horndog@HornDogsHouse:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           504        427         76          0         31        233
-/+ buffers/cache:        162        341
Swap:         1474          0       1474  <--------

```

As you can see, I have a total of 1474 available.
Yours is 0. I guess your Swap is not recognized.

---

### Post by soulestream on 2006-01-09
heh, forgot something

if its /dev/hda6, then 

mkswap /dev/hda6  <--**
swapon -a 

my fstab looks like this

/dev/hda2 swap swap defaults  0  0

thats on Arch, but should be the same

soule

---

### Post by tatacalu on 2006-01-09
something's wrong...

in the console I wrote: **mkswap -L MySwap /dev/hda6**
everything ok... but when I entered **free -m**
the result was still:
```
             total       used       free     shared    buffers     cached
Mem:           503        430         73          0         21        256
-/+ buffers/cache:        152        351
Swap:            0          0          0

```

no idea...

---

### Post by soulestream on 2006-01-10
after you did mkswap, did you do a swapon /dev/hda6


soule

---

