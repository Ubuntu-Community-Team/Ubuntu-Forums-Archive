---
title: "How can I install &quot;Office Bibliothek&quot;?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Osmodia on 2005-10-13
I can't start the "Office Bibliothek". I've got no problems under ubuntu 5.04.

[Download](http://www.office-bibliothek.de/index2.html?service/st_update.html).

I've tried to install the tar.gz and also tried to convert the rpm2deb. Installation works, but I can't get the program running.

> 
# officebib
xset:  bad font path element (#259), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
/opt/officebib/officebib.bin: /opt/officebib/libgcc_s.so.1: version `GCC_3.3' not found (required by /usr/lib/libstdc++.so.6)
xset:  warning, no entries deleted from font path.


---

### Post by Osmodia on 2005-10-14
No answers? Can somebody test it? Its free :rolleyes:

---

### Post by nilfilter on 2005-10-23
[QUOTE=Osmodia]No answers? Can somebody test it? [/QUOTE]You need to remove both */opt/officebib/libgcc_s.so.1* and */opt/officebib/libstdc++.so.5*. 

[QUOTE=Osmodia]Its free :rolleyes:[/QUOTE]Not quite so. You can download the program but it doesn't come with data files which need to be purchased separately.

---

### Post by bootleg on 2005-10-24
@nilfilter

Thanks.

---

