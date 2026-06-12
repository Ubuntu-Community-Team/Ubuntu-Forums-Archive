---
title: "nwn linux client problem"
date: 2005-10-26
forum: Gaming &amp; Leisure
---

### Post by dphipps on 2005-10-26
I have downloaded and extracted the contents of the Linux Client Resources into /home/dphipps/nwn/ and the linux binaries into the same file.  However when I try to run it this is what I get ```
dphipps@phipps1:~/nwn$ ./nwn
Error
dphipps@phipps1:~/nwn$ ./nwmain
./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory
dphipps@phipps1:~/nwn$

```  Does anybody know what I might have done wrong?  I would provide more information but I don't know that information I should provide.

---

### Post by Koybe on 2005-10-26
Be sure you've put it in the same directory and not something like :
/home/dphipps/nwn/ for de ressources and /home/dphipps/nwn/nwn/ for the binaries.

If you can't get it work use this [link](http://nwn.bioware.com/downloads/linuxclient.html) from bioware, don't forget to update to the latest version (1.65).

It works fine for me but my WS is still in FC4 only my laptop is using ubuntu at the moment, and i'm also using nwn+sou+hou.

---

### Post by dphipps on 2005-10-26
I downloaded and installed the update.  Now when I run ./nwn I get this.
```
dphipps@phipps1:~/nwn$ ./nwn
Failed to initialize graphics.
dphipps@phipps1:~/nwn$

```

---

### Post by drfalkor on 2005-10-26
do you have the graphic drivers installed ? :confused:

---

