---
title: "Installation not able to complete"
date: 2011-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by newbie92 on 2011-01-12
When i try to install the latest maveric version of xubuntu, initially the installation looks just fine. But after almost 50% completion, a message pops up 
" an error occured
C:\docume~1\admin\local~1\temp\wubi10.10-rev197.log "

Pls help me. Im trying to make my computer windows free.

Pc config,
Pentium3 866MHz,
256 Mb ram

---

### Post by newbie92 on 2011-01-12
The installation stops all the sudden in the middle showing an error
"C:\docume~1\admiin\local~1\temp\wubi-10.10-rev197.log"

Pentium3 866MHz
256 Mb ram

---

### Post by bcbc on 2011-01-13
that's not the error - it's the log file.

Download the CD image (.iso) file and wubi.exe into the same folder and run wubi from there. Make sure you get the same release of each. i.e. for 10.10 get them from here [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

---

### Post by s.fox on 2011-01-13
Please do not create duplicate threads.  Thank you.

Threads Merged.

---

### Post by bcbc on 2011-01-13
> **newbie92 said:**
> Pls help me. Im trying to make my computer windows free.

Pc config,
Pentium3 866MHz,
256 Mb ram

Wubi is not the way to go if you want to be 'windows free'.

Also, you can't install xubuntu with the wubi.exe on [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) - it won't work as it's at 'release' 10.04.1 there is no 10.04.1 version of xubuntu.

In addition - you only have 256MB ram. Assuming that's all available to you it might work, but chances are some is being used. So you're better off installing lubuntu (I have no experience with this).

---

