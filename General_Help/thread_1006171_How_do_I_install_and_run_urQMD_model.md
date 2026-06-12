---
title: "How do I install and run urQMD model?"
date: 2008-12-08
forum: General Help
---

### Post by fawadzafar on 2008-12-08
how can i install .tar.gz file in ubuntu which is downloaded from internet.

---

### Post by cmay on 2008-12-08
depends on what it is. and i would suggest that you do not download stuff from the internet  and just use the add/remove menu for installing programs. 

the tar.gz files can be unpacked very easy using the default archive manager.
if it is a theme from gnome.org then it should NOT be unpacked but installed using the thmes manager. please post some more info and it it will be more easuy to help you. :)

---

### Post by Oceanic on 2008-12-08
tar 
means that (several) files are "glued" together
with the program  tar, so in essence an archive

gz 
is the compression that is used (gzip)
bzip or zip are other options to make the archive smaller

Indeed generally do not open/install from the internet but use the repositories instead :-)

Do you have a link for us where you downloaded that .tar.gz from?

---

### Post by 3rdalbum on 2008-12-08
Have you tried:

1. Looking for the program in the repositories?
2. Looking for a version of the program that has been packaged up as a .deb?
3. Extracting the tar gzip file and following the instructions within?

---

### Post by fawadzafar on 2008-12-09
how can i install/run urQMD model in ubuntu which is in fortran language.

---

### Post by fawadzafar on 2008-12-10
I have urQMD model in .tar.gz file.how can i install it in ubuntu.

---

### Post by fawadzafar on 2008-12-10
how .tar.gz file is installed in ubuntu

---

### Post by taurus on 2008-12-10
Maybe this helps especially Step 2.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by oldos2er on 2008-12-10
It depends on what the tar.gz contains.

---

### Post by ibutho on 2008-12-10
Usually tarballs (tar.gz, tar.bz2, etc) have a README or INSTALL file inside that has the installation instructions and any required dependencies.

---

### Post by MattBD on 2008-12-10
A tar file is like a zip file in Windows ie. it's an archive of other files. You can extract it by right-clicking in Nautilus, or from the command line like this:
```
tar -xzf tarfilename
```
for tar.gz or tar.gz2. If it's bz or bz2, use this instead:
```
tar -xjf tarfilename
```
If it's software that you're looking to install, like ibutho said there will be a README or INSTALL file in the tar file.
However, if you're looking to install software, it's better to use Ubuntu's built in package manager - check out [this link]("https://help.ubuntu.com/8.04/add-applications/C/index.html") for details. I really wouldn't get into installing tar files you've downloaded off the web until you're reasonably experienced. There also might be a deb package (Ubuntu's native software package format) for what you're after at [http://www.getdeb.net/](http://www.getdeb.net/)

---

