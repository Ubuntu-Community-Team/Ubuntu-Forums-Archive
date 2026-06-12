---
title: "Limewire won't open"
date: 2005-10-03
forum: Desktop Environments
---

### Post by zac851 on 2005-10-03
I used the directions off of ubuntuguide.org to download and install limewire.  Everything seems to go well.  After I completed all the steps that were given.  I went to K Menu > Internet > Limewire and clicked on it.  When I click on it, something pops up on the taskbar like its loading something then It just goes away after about 20 seconds and nothing happens.  I uninstalled it and reinstalled but this didnt help any.  What else can I do to get this working?    THanks.

[img]http://www.turboinduction.com/misc/snapshot1.jpg[/img]

---

### Post by SGC on 2005-10-03
Open konsole (kmenu -> system -> konsole), and type **limewire**, post the error message you get here.

---

### Post by zac851 on 2005-10-03
bash: limewire: command not found     ?

---

### Post by fourchannel on 2005-10-03
that means that limewire is not in your path. you can do a few things:

On the guide that showed you how to install limewire, find out where it actually installed it. then go to that directory and see if you can launch it from a konsole there. e.g. 

*assuming your in the directory where it's installed*  
$ ./limewire  (or whatever it is named)

if that works, then go to your KDE menu editor and edit LImeWire's launch command from
 [ limewire ]
 to
 [ /the.directory.where.you.installed.it/limewire ] or whatever it is named.

hope that helps.

---

### Post by zac851 on 2005-10-04
Ok I just did that and heres the error that I got.  Do you think its just because of the java not installed thats causing all of this?

root@linuxbox:/opt/LimeWire# ./runLime.sh
Starting LimeWire...
Java exec not found in PATH, starting auto-search...
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
root@linuxbox:/opt/LimeWire#

---

### Post by tehwa on 2005-10-04
If java is not installed, Limewire will not run.

Verify that it is installed by running
```
java -version
```

---

### Post by zac851 on 2005-10-04
Hmm Now I'm not sure what to do.  I installed java.  Everything went fine.  
> zac851@linuxbox:~$ java -version
java version "1.4.2"
gcj-4.0 (GCC) 4.0.0 20050301 (prerelease) (Debian 4.0-0pre6ubuntu7)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

So I figured everything would work.   This is what I did next.

> zac851@linuxbox:~$ runLime.sh
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com) 

Now what are my options?

---

### Post by mlomker on 2005-10-04
> So I figured everything would work.   This is what I did next.


Most java programs will only run with Sun's java.  [Here are the steps.]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=sun+jre+.bin")

---

### Post by zac851 on 2005-10-04
Thanks that worked perfect.

---

