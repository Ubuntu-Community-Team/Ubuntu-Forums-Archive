---
title: "mlabel: Long file name already exists"
date: 2008-12-04
forum: General Help
---

### Post by HyperHacker on 2008-12-04
This just had me wondering:```
hyperhacker@mercury:~$ sudo mlabel -i /dev/sdg1 ::
 Volume has no label
Enter the new volume label : PSP
Long file name "PSP" already exists.
```OK, yes, there is a "PSP" directory in the root, but why does that matter? I thought the FAT32 labels were stored separately from the filenames?

Also, this seems like a bug:```
hyperhacker@mercury:~$ sudo mlabel -i /dev/sdg1 ::
 Volume label is PSPMS      
Enter the new volume label : ^C^C^C^[^[
Long file name "" contains illegal character(s).
a)utorename A)utorename-all r)ename R)ename-all 
s)kip S)kip-all q)uit (aArRsSq): q
```It wouldn't let me quit, so I just hit Enter. Even though I told it to quit it went ahead and renamed the disk to \x0A\x0A (even though that's nowhere near what I entered). Easy to fix, but I don't think it should be doing that...

---

### Post by psusi on 2008-12-05
Fat stores the volume label as a file entry in the root directory that has no data and a special bit set in its attribute byte, hence the conflict with the directory of the same name.

---

### Post by airydragon on 2009-09-24
> **psusi said:**
> Fat stores the volume label as a file entry in the root directory that has no data and a special bit set in its attribute byte, hence the conflict with the directory of the same name.

how windows can manage it but linux? weird.

my solution is something like that:
```

sudo su #be sudo for permissions
cd /media/disk/ #my stick mounted there, change the path for your system
mv PSP PSPx # rename the PSP directory 
mlabel -i /dev/sdh1 -s ::PSP # change the label of memory stick (my stick is /dev/sdh)
mv PSPx PSP # rename back the directory
cd #get out of memory stick

```
umount, unplug and plug it again. voila

---

