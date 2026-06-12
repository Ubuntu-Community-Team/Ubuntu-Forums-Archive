---
title: "Can't see files on disk"
date: 2005-12-16
forum: General Help
---

### Post by tanari on 2005-12-16
I have written CDRW with **graveman**, under windows I can see files, which     I have written, but under linux can't! Also I can see them in **NeroLINUX**, after importing old session!! Very strange. :confused: 
I have HP dvd640 DVDRW

Has somebody the same problems?

---

### Post by earobinson on 2005-12-16
When you put the cd in dose linux reckognise that there is a CD? Also are you putting the cd back into the cd burner or a dvd drive?

Have you tried turning [DMA]("https://wiki.ubuntu.com/DMA?highlight=%28dma%29") on?

---

### Post by tanari on 2005-12-16
In about 2 hours I have sold this problem :)
Maybe it is graveman specific problem, but I don't know.

Who use graveman and have problems with multisession CD-R(W)s can try this:
*in settings tab*
1) choose **TAO** mode for writing CD-R(W)s
2) check **Start or continiue multi session CD**
3) don't check/uncheck **Do not fixate the disk after writing** - my problem was with this option
  first try simulate write

Also I made changes in fstab. Added **ro** to my DVDRW drive
> 
/dev/hdc        /media/cdrom0   udf,iso9660 **ro**,user,noauto     0       0


But I don't know how it helps, maybe doesn't help.

Good luck :)

---

### Post by earobinson on 2005-12-16
sold = solved?

---

### Post by tanari on 2005-12-16
oh, sorry :oops:. *Solved * is right,
sorry again for my bad english ](*,).

Now I don't have problems with CD writing.
But I can't create multisession DVD and format DVD :(. 
When I try to format DVD **graveman** always says *"Media is already formated!"*, **gnomebaker** has this output
```

* DVD&#177;RW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
* 4.7GB DVD+RW media detected.
- illegal command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

```


-----------
*And one more...*

> 
tanari@ubuntu:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
tanari@ubuntu:~$


What means **HDIO_GETGEO failed: Invalid argument**?

---

