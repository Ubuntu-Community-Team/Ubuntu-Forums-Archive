---
title: "[SOLVED] Hibernate/swap problem"
date: 2009-01-04
forum: General Help
---

### Post by footprint on 2009-01-04
Hibernate has stopped working(I don't know when as I haven't used it for a while).
The error messages indicate there is no active swap partition.
I can't activate swap using "swapon -a" as root, but I can activate it by clicking <swapon> in GParted and hibernate then Works. However on reboot the swap partition is no longer active. Following the forum thread I removed the UUID from fstab but this has achieved nothing.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=34458741-dd01-48fa-88d6-e95d1577c2c3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0c5fd73a-18e5-4b3b-be54-416f13286d17 /home           ext3    relatime        0       2
# /dev/sda7                               none            swap    sw              0       0

------------------------
martin@martin-netbook:~$ free
             total       used       free     shared    buffers     cached
Mem:       1024248     662204     362044          0      23344     287928
-/+ buffers/cache:     350932     673316
Swap:            0          0          0
martin@martin-netbook:~$ 

--------------------------
after activating swap from GParted:-
martin@martin-netbook:~$ free
             total       used       free     shared    buffers     cached
Mem:       1024248     731948     292300          0      31396     322288
-/+ buffers/cache:     378264     645984
Swap:      1269092          0    1269092
martin@martin-netbook:~$ 

I don't realy want to have to reinstall.

---

### Post by Elfy on 2009-01-04
Can you post results of these commands please

```
sudo fdisk -l
blkid
```

---

### Post by azr on 2009-01-04
You've commented out the line that mounts the swap partition. 
To uncomment it remove the # from the begining of this line: 

```
# /dev/sda7 none swap sw 0 0
```

Then use ```
 swapon -a 
```

(Did you change the UUID of your swap partition to /dev/sda7 ?)

---

### Post by Elfy on 2009-01-04
I did in fact that but wanteed to make sure that the partition actually existed :)

---

### Post by footprint on 2009-01-04
When I deleted the UUID info I should have remove the # from the /dev/sda7.

Silly me. All now working again.

Thanks azr & forestpixie. (How do I mark the thread as solved?)

---

### Post by Elfy on 2009-01-04
There's a link in my sig to solve threads

---

