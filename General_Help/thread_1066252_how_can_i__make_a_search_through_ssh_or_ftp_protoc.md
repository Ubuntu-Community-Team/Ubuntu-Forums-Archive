---
title: "how can i  make a search through ssh or ftp protocol"
date: 2009-02-10
forum: General Help
---

### Post by malanco on 2009-02-10
hi guys i need a little help here, i have a class at college; my professor uploaded the exam into a fedora server, he says if we can find it we can start it right away, im 2 days away from the test, i need to know how to search some specific file extensions, make a search through ssh or make a search through my ftp client how can i do this??.

thanks!!

---

### Post by fava on 2009-02-10
You can mount the remote drive locally by using shfs, there is also similar tools for ftp.

-or-

You can mount the remote drive using midnight commander and use the internal searching/browsing tools with the command:

mc  /#ftp:hostname.com/directory

---

### Post by dcstar on 2009-02-10
> **malanco said:**
> hi guys i need a little help here, i have a class at college; my professor uploaded the exam into a fedora server, he says if we can find it we can start it right away, im 2 days away from the test, i need to know how to search some specific file extensions, make a search through ssh or make a search through my ftp client how can i do this??.

thanks!!

```
ls *extension-name
``` works in every command line FTP client I've used, and graphical FTP clients provide other ways to achieve this.

---

### Post by Gunman1982 on 2009-02-10
Just run a 'find -name *.pdf' (only if its a pdf of course ;-) ) through a ssh console, it will search from the directory tree you execute it in. So you may want to change the directory first or search under another directory with 'find /home/profs_name_whatever/ -name *.pdf'.

---

### Post by wirelessmonkey on 2009-02-10
Just for fun, I'd try ```
 sudo find / | grep *.extension 
```
which will search the entire drive for your file, but be aware you'll get a bunch of errors from directories that you're not allowed access to.

---

### Post by malanco on 2009-02-19
thank you all guys, lol i founded the exam like 1 hour before the test .

---

### Post by jonobr on 2009-02-19
10 minutes .......... study study study.............


Best of luck in your exam........

---

