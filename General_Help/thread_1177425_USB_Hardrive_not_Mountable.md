---
title: "USB Hardrive not Mountable"
date: 2009-06-03
forum: General Help
---

### Post by styks1987 on 2009-06-03
I plugged a Hard Drive, that has been used on a mac, into my Vista system. It told me i needed to write a MBR to be able to use it. So i did and it shows no data on the hard drive. I don;t have access to the Mac right now. So I tried to load the drive into Ubuntu but it will not mount the drive. It says unable to mount location.

It is a Western Digital MyBook and I am using the latest Ubuntu.

I just need to copy some files off of the drive. Did I already erase everything by writing the MBR?

Thanks 
Mike

---

### Post by pawnrocket on 2009-06-03
It sounds like I all you wrote to was the Master Boot Record.

which filesystem?

If you didn't reformat the book to something else it is FAT32.

---

### Post by styks1987 on 2009-06-03
since it didn't automatically mount in vista i believe it is probably HPFS. That is what it shows up as under ubuntu.

Thanks for you help,

Mike

---

### Post by whoop on 2009-06-03
Really weird that vista wrote an MBR to it... You don't need to boot from it to read it.

what's the output of
```

sudo blkid

```

also check with the partition editor if you can find out anything about the drive
```

gksudo gparted

```

---

### Post by styks1987 on 2009-06-03
Only the internal Hardrive shows up for the *blkid*

and

for Gparted I get only unpartitioned space.

Thanks
Mike

---

### Post by styks1987 on 2009-06-03
Why is this just showing up as unpartitioned space? I know there is a lot of information on the drive.

Mike

---

### Post by styks1987 on 2009-06-03
Ok i just decided to use MacDrive7. They have a trial. Worked perfectly.

Mike

---

