---
title: "Compiz-settings 64bit"
date: 2007-06-21
forum: Desktop Effects &amp; Customization
---

### Post by maino82 on 2007-06-21
Does anyone know if there's eithe  a precompiled binary for the amd64 arch or source code for the compiz-settings program? The links over at the compiz page ( [http://forum.compiz.org/viewtopic.php?t=153&highlight=compizsettings](http://forum.compiz.org/viewtopic.php?t=153&highlight=compizsettings) ) seem to be broken, and all the .deb files I've been able to find have all been i386, which dpkg keeps spitting back at me saying it's the wrong arch. Any suggestions or links to source/debs would be greatly appreciated!

Thanks,
Dave

---

### Post by maino82 on 2007-06-22
OK so I finally got it working in case anyone has the same problem that I did.

First, I forced the deb to install:

```
sudo dpkg -i --force-architecture compiz-setting-i386.deb
```

Then I had to go through the Ubuntu package list and find all the 386 versions of files that it told me were the wrong ELF class. Then I extracted those files from the debs (dpkg -x or you can just open the deb with the archive manager) and moved them into my /usr/lib32 folder. Eventually, after doing this for about 6 or 7 files, it worked!

This process should work for forcing any 386 package to run on a 64bit machine. Hope it's helpful!

---

