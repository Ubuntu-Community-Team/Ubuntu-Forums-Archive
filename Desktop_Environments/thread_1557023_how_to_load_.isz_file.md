---
title: "how to load .isz file?"
date: 2010-08-20
forum: Desktop Environments
---

### Post by riversmall on 2010-08-20
As we known, [COLOR=red]**.isz**[/COLOR] file is compressed by [COLOR=red]UltraISO[/COLOR].
 
how to load it under ubuntu? 
 
Are there any applications for it?

---

### Post by lykeion on 2010-08-20
You could try poweriso. The have a free linux command line utility to convert image files. 
I'm not totally sure it supports lsz, but do try and find out for yourself.

1. download poweriso
[http://www.poweriso.com/poweriso-1.3.tar.gz](http://www.poweriso.com/poweriso-1.3.tar.gz)

2. extract it and open a terminal in that dir

3. convert the file
> poweriso convert file.lsz -o file.iso -ot iso

4. burn or mount the iso image
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/MountIso#Mounting%20ISO%20Files](https://help.ubuntu.com/community/MountIso#Mounting%20ISO%20Files)

Hope this helps...(and if so please mark this thread as SOLVED)

---

### Post by mastermindg on 2010-11-08
Sorry...nogo on PowerISO

```
~/Downloads$ ./poweriso convert testfile.isz -o testfile.iso -ot iso

PowerISO   Copyright(C) 2004-2008 PowerISO Computing, Inc
            Type poweriso -? for help

testfile.isz: The file format is invalid or unsupported.
```

---

