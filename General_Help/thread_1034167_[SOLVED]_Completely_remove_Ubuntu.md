---
title: "[SOLVED] Completely remove Ubuntu"
date: 2009-01-08
forum: General Help
---

### Post by upapilot on 2009-01-08
Hi guys!
I have a friend who wants to get rid of Ubuntu on his PC and merge the Ubuntu partition into the Windows partition......How can one safely do this?:confused:

---

### Post by melojo on 2009-01-08
open a terminal this will restore windows mbr and then you can use the ubuntu cd to repartition and merge with windows.  You should back up all important data!!
```
sudo lilo -M /dev/sda mbr
```

assuming that windows is on the drive sda

---

### Post by upapilot on 2009-01-08
I meant to say just DELETE ubuntu and it's PARTITION

---

### Post by melojo on 2009-01-08
You can go to the link below and download the live cd that will boot into gparted or use the gparted thats on the ubuntu cd.  All you have to do is to delete the partition create a new one then format it.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by sendblink23 on 2009-01-08
> **melojo said:**
> You can go to the link below and download the live cd that will boot into gparted or use the gparted thats on the ubuntu cd.  All you have to do is to delete the partition create a new one then format it.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)



Don't forget to mention him.. to run this command... (LIVECD)  after  he  Re .. partitions back.. the original Hard drive for his Windows...   inside  Gparted



sudo lilo -M /dev/sda mbr


So that he can get back his Original Windows Boot  of the computer (it will eliminate the Grub menu list Boot)

---

### Post by melojo on 2009-01-08
> **sendblink23 said:**
> Don't forget to mention him.. to run this command... (LIVECD)  after  he  Re .. partitions back.. the original Hard drive for his Windows...   inside  Gparted



sudo lilo -M /dev/sda mbr


So that he can get back his Original Windows Boot  of the computer (it will eliminate the Grub menu list Boot)

mentioned on the second post.

---

### Post by sendblink23 on 2009-01-08
> **melojo said:**
> mentioned on the second post.

You forgot to mention.. what does that command  do .. you have to explain it..   *noobs  to learn  what  certain commands do

---

### Post by upapilot on 2009-01-09
Where are we supposed to enter this command "sudo......"? in the Windows terminal or in the terminal of the Ubuntu booted from the live CD?

---

### Post by melojo on 2009-01-10
no need to use the live cd just open a terminal and type

sudo lilo -M /dev/sda mbr

---

### Post by upapilot on 2009-01-10
Hey when i type the above mentioned command it gets some fatal error!

---

### Post by upapilot on 2009-01-10
the error is:
Fatal: /dev/sda2 is not a master device with a primary parition table

---

### Post by sendblink23 on 2009-01-11
> **upapilot said:**
> the error is:
Fatal: /dev/sda2 is not a master device with a primary parition table

Try to do it ...  with the Live CD instead

That worked perfectly for me...

All what that command does is.. to ERASE  GRUB.. and Bring back the original WINDOWS Booting of your computer

Now after making that command: [COLOR="Red"]sudo lilo -M /dev/sda mbr[/COLOR]

Shutdown inside LiveCD (take it off when mentioned)

Simply Restart your computer, to see if it automatically boots normally as originally did when it was only Windows in your computer.

If that is correct..

then Insert again  the LiveCD .. and restart the computer ...

Run Ubuntu ...  and this time head inside and in the TOP go to Systems.. and inside one of those  not sure if its Preferences or Administration.. but you should read  GParted 

Once in there Erase all Linux(Ubuntu's) partitions   Ext3 & Swap ... After deleting them...   just EXPAND COMPLETELY..  the Windows Partition .. and Click APPLY

After that is done ...  close it

And Shut Down from LiveCD (remove CD again after mentioned)

And well let the computer boot normally  and the blue screen of nFdisk ...  something like that will run..   that is normall, its to ensure that your Hard Drive .. is all alright ...   let it run .. after it end .. you will be brought back normally to Windows

And Yes do check MY COMPUTER  to make sure your C:/   drive is back to normal to its original Hard Drive GB space.

And you are done

---

### Post by melojo on 2009-01-11
post the ouput of

```

sudo fdisk -l

```

Below is a link to super grub disk, if you want to use that.  You will have to burn the iso.    [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by upapilot on 2009-01-12
He guys sorry!!!! The entire problem was caused by a completely silly typing mistake of mine!
Sorry Again):P

---

