---
title: "Quake 3 132b no ./config, make, or shellscript?"
date: 2006-02-20
forum: Gaming &amp; Leisure
---

### Post by threethirty on 2006-02-20
how does one go about installing from source without the above mentioned files?

---

### Post by threethirty on 2006-02-20
I tried to install the .deb from here:
[http://wwwcip.informatik.uni-erlangen.de/~sibrklei/ubuntu/breezy/]("http://wwwcip.informatik.uni-erlangen.de/~sibrklei/ubuntu/breezy/")
and this is what Konsol spit out at me

```
three@CondorV2:~$ sudo dpkg -i quake3_1.33+SVN470-0ubuntu1_i386.deb
Selecting previously deselected package quake3.
(Reading database ... 89557 files and directories currently installed.)
Unpacking quake3 (from quake3_1.33+SVN470-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of quake3:
 quake3 depends on libopenal0; however:
  Package libopenal0 is not installed.
 quake3 depends on quake3-data; however:
  Package quake3-data is not installed.
dpkg: error processing quake3 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 quake3

```

---

### Post by R3linquish3r on 2006-03-03
This way worked flawlessly for me:

Download the patch from here:
[http://www.fileshack.com/file.x?fid=1289](http://www.fileshack.com/file.x?fid=1289)

Save it to home.

Put this in console:
```
chmod +x linuxq3apoint-1.32b.x86.run
```

Then:
```
sudo ./linuxq3apoint-1.32b.x86.run
```

Install :)

---

