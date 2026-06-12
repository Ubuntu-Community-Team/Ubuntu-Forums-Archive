---
title: "Compiling tar.gz in Ubuntu error"
date: 2009-06-06
forum: General Help
---

### Post by quesman on 2009-06-06
I downloaded a .tar.gz file on Ubuntu, and unzipped it. But then when i navigated to the unzipped folder and typed ./configure, it just said:

alex-goldstein@AJ-Desktop:~/Desktop/gnump3d-3.0$ ./configure
bash: ./configure: No such file or directory

Why does it do this? Any way to fix this or get around it?

Thanks!

---

### Post by ad_267 on 2009-06-06
The ./configure etc method doesn't work for all archives. A tar.gz is just like a zip file, it could contain anything. Have a look at what was extracted. There might be a README or INSTALL file you can read.

Edit: Read the INSTALL file myself:
> INSTALLATION
============

  GNUMP3d installation should require no more than the 
 following:-

	make install

  This will install the software in /usr/bin, with the
 configuration files in /etc/gnump3d/


Of course you have to be root, so that will be "sudo make install"

---

### Post by colau on 2009-06-06
> **quesman said:**
> I downloaded a .tar.gz file on Ubuntu, and unzipped it. But then when i navigated to the unzipped folder and typed ./configure, it just said:

alex-goldstein@AJ-Desktop:~/Desktop/gnump3d-3.0$ ./configure
bash: ./configure: No such file or directory

Why does it do this? Any way to fix this or get around it?

Thanks!


Going to that directory can you post
```

ls

```;)

---

