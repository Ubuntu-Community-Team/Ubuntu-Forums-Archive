---
title: "Can't remove conexant package"
date: 2009-02-25
forum: General Help
---

### Post by svenofix on 2009-02-25
I was trying to get dial-up to work with ubuntu 8.1, so I was trying different stuff out. One thing I tried was installing 'conexant_192-1ubuntu-1_i386.deb', now however I am unable to remove the package (I think it didn't install properly or something). DPKG constantly reports an error, as well as most other package managers; update manager wants to do a partial upgrade, but crashes when I try it. I've tried purging DPKG with 'sudo dpkg --purge remove conexant', I think however it did more harm than good.

Now I'm stuck with numerous problems, I can't use update manager to download and install the rest of the updates available; when installing a package, the installer will also try and setup conexant and in most cases won't work at all; ADD/REMOVE is out of order. The only thing that seems to work is synaptic.

EDIT: I'm unable to mark packages for install in ADD/REMOVE

So, any ideas?

Thx,
Svenofix

---

### Post by ibuclaw on 2009-02-25
try:
```
sudo dpkg --configure -a
```
followed by:
```
sudo apt-get install -f
```
and tell us how that goes (post any erraneous output, if possible)

Regards
Iain

---

### Post by svenofix on 2009-02-25
This is what I get:

```
svenofix@Monkey:~$ sudo dpkg --configure -a
svenofix@Monkey:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  conexant
0 upgraded, 0 newly installed, 1 to remove and 32 not upgraded.
1 not fully installed or removed.
After this operation, 1851kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118273 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant
E: Sub-process /usr/bin/dpkg returned an error code (1)
svenofix@Monkey:~$ 
```

EDIT: When I try to install a .deb file (in this case Songbird by Mozilla) the installer first tries to remove conexant which gives much the same output as shown above. In addition a pop-up comes up saying:
```

Could not install all dependencies

installArchives() failed
```

---

### Post by svenofix on 2009-02-26
I finally solved the problem!!\\:D/
I followed what la leche jodia wrote towards the end: [http://ubuntuforums.org/showthread.php?t=77492](http://ubuntuforums.org/showthread.php?t=77492)
In other words I deleted any files on conexant in /var/lib/dpkg/info and deleted the entry for the conexant package in /var/lib/dpkg/'status'. It did the trick. I am now able to update properly and all my other problems should be gone as well (yet to properly check it).

---

### Post by zosky on 2010-06-30
thanks yall. 

this helped, but i didnt do exactly as the last user. 

[LIST=1][*]edit **/var/lib/dpkg/info/conexant.postrm**
comment out line 23... "#rmmod hsfserial hsfengine hsfbasic2 hsfosspec"
[*]*$sudo apt-get purge conexant*
[*]*$sudo rmmod  hsfusbcd2 hsfmc97sis hsfmc97ati hsfmc97ali hsfmc97via hsfmc97ich hsfpcibasic3 hsfserial hsfengine hsfbasic2*
[/LIST]

---

