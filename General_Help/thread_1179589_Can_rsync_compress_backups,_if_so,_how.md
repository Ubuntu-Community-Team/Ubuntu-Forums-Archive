---
title: "Can rsync compress backups, if so, how?"
date: 2009-06-05
forum: General Help
---

### Post by rcayea on 2009-06-05
So when I backup my files, even just my important ones, I end up with a lot of space taken up because I can't get rsync to compress the files during backup. Is there a way to do this?

Is there an automatic compression option for files that are X-days old, like Windows has the option to compress old files to save room?

Any thoughts?

Thanks,
Randy

---

### Post by rcayea on 2009-06-05
bump

---

### Post by blueridgedog on 2009-06-05
Rsync is designed to keep groups of files synchronized.  For compression and archival, tar is the tool you want.  The downside to that is that you need to backup versus synchronize.  I prefer to synchronize as it is faster, so I just use a few cheap disks via a sata hot swap port.  I have some tar scripts that keep 5 copies if you want to have something to hack away at (at least I think I can find them...with the price of drives so low, I have not done a tar backup in six years).

---

### Post by rcayea on 2009-06-06
blueridgedog,

Thanks for the info. I had known tar was something used to package programs and the like, but it never crossed my brain to use it as a tool for personal compressions. 

thanks,
RAndy

---

### Post by Legace on 2009-06-06
You could use the z switch:

```
 -z, --compress              compress file data during the transfer
     --compress-level=NUM    explicitly set compression level

```

---

### Post by rcayea on 2009-06-08
thanks Legace,

I'll look into that. It seems promising.

---

### Post by unutbu on 2009-06-08
rcayea, the -z flag will compress the files during transfer, but the files are uncompressed in the backup directory. It may help when transferring data over slow connections, but I'm not sure that is what you are looking for.

Note that if you use tar or some other compression program on the files in the backup directory, then the next time you use rsync, rsync will mistakenly believe those files do not exist and will transfer them again. 

So instead of saving space, you might end up using even more space than if you did no compression at all.

If you'd like to compress and use rsync, perhaps it is best to compress things on the source side before using rsync.

As an alternative to tar, you could do this:

To compress files that haven't been modified for 2 days or more, you could run 
```

find /path/to/source -mtime +2 -exec bzip2 {} \;
```

And to uncompress them, 
```

find /path/to/source -name "*.bz2" -exec bunzip2 {} \;

```

---

### Post by rcayea on 2009-06-08
unutbu,

In essence, what you are (graciously) proposing with the command line suggestions, is about as close as I'll get to having files that have not been used in a while compressed without simply being duplicates, i.e: same size?

If I am understanding you correctly, I'll try those commands. 

Thanks,
Randy

---

### Post by unutbu on 2009-06-08
Right,
```

find /path/to/source -mtime +2 -exec bzip2 {} \;
```

will find all files in /path/to/source (or any of its subdirectories) which have not been modified for at least 2 days. (If you wish to change that to say 7 days, then change "-mtime +2" to "-mtime +7"). 

The "-exec bzip2 {} \;" tells the find command to run  bzip2 on each file it finds (which has not been modifiied for at least two days). The "{}" gets replaced by the name of each file.

---

