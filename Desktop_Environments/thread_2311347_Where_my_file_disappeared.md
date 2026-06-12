---
title: "Where my file disappeared?"
date: 2016-01-26
forum: Desktop Environments
---

### Post by Grigoriy on 2016-01-26
Hello!

I was trying to download 1.1 GB file from MEGA cloud storage. In the  beginning, I didn't get a "Save As" nautilus window as usual. Though the  file was actually downloading to my system. Then I got a small window  with an option to save, but I closed that window (had to press "Save"  button to choose the location for the file). And that's it. Can't find  this file anywhere. Neither in the Downloads folder, nor in Firefox's  cache folder, which is even smaller than 1 GB in size. But in GParted I  see that the free space in my /home partition became about that file's  size smaller nevertheless.

---

### Post by egeezer on 2016-01-26
Open a terminal and type the two-letter command  	Code:
 	ls 
That will show you the files in your home folder.  One of them should be the download.

---

### Post by matt_symes on 2016-01-26
Hi

Open a terminal and type

```
find ~ -size +1G -print 
```

You can adjust the +1G as required.

From *man find*

```

       -size n[cwbkMG]
              File uses n units of space, rounding up.  The following suffixes can be used:

              `b'    for 512-byte blocks (this is the default if no suffix is used)

              `c'    for bytes

              `w'    for two-byte words

              `k'    for Kilobytes (units of 1024 bytes)

              `M'    for Megabytes (units of 1048576 bytes)

              `G'    for Gigabytes (units of 1073741824 bytes)

              The size does not count indirect blocks, but it does count blocks in sparse  files  that  are  not  actually
              allocated.   Bear  in  mind  that the `%k' and `%b' format specifiers of -printf handle sparse files differ&#8208;
              ently.  The `b' suffix always denotes 512-byte blocks and never 1 Kilobyte blocks, which is different to the
              behaviour  of -ls.  The + and - prefixes signify greater than and less than, as usual, but bear in mind that
              the size is rounded up to the next unit (so a 1-byte file is not matched by -size -1M).
```

**EDIT:**

Example:

```
matthew-xu-16-04:/home/matthew:1 % ls -lh xubuntu-15.10-desktop-amd64.iso
-rw-rw-r-- 1 matthew matthew 1.1G Jan 26 18:41 xubuntu-15.10-desktop-amd64.iso
matthew-xu-16-04:/home/matthew:1 % 
```

```

matthew-xu-16-04:/home/matthew:1 % find ~ -size +1G -print               
<..snip..>
/home/matthew/xubuntu-15.10-desktop-amd64.iso
matthew-xu-16-04:/home/matthew:1 %

```

Kind regards

---

### Post by Grigoriy on 2016-01-26
Thank you both for your replies!

Can't find it, but that's okay. I would know from now on how MEGA downloads its (ie., my) files.

---

### Post by matt_symes on 2016-01-26
Hi

> Can't find it, but that's okay.

Seriously ?

Did you try adjusting the size parameter ?

Did mega unlink the file while downloading ?

If you reboot (or close the browser or its page), do you regain the space that looks to have been lost ?

Are you 100% sure the download completed successfully ? Because if it did, the file has to be on your system somewhere, even if it's unlinked (although the space will be reclaimed after process that downloaded the file is killed, if it is unlinked ) ?

Kind regards

---

### Post by Nuno_Abreu on 2016-01-27
Did you try to check in the /tmp directory?

---

### Post by matt_symes on 2016-01-27
Hi

> **Nuno_Abreu said:**
> Did you try to check in the /tmp directory?

This is a good suggestion apart from

> But in GParted I see that the free space in my /home partition became about that file's size smaller nevertheless. 

The OP seems to be suggesting it may not be in /tmp, unless the OP has remounted it or something, or /home is not a separate partition.

/tmp is usually a good place to look though.

Kind regards

---

### Post by Nuno_Abreu on 2016-01-28
> **matt_symes said:**
> The OP seems to be suggesting it may not be in /tmp, unless the OP has remounted it or something, or /home is not a separate partition.

/tmp is usually a good place to look though.

Kind regards

Still, I'd recommend it - it could also be in the system cache, but I'm pretty it is not. I advise the OP to check the contents in the .cache folder in the /home directory.

---

