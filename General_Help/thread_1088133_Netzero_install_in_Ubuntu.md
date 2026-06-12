---
title: "Netzero install in Ubuntu"
date: 2009-03-05
forum: General Help
---

### Post by jeff35 on 2009-03-05
I have a Netzero. deb file that was designed for Linspire. Could someone help me install it in Ubuntu? This is the instructions from Netzero:

# After downloading the installation file it will have a .deb extension (eg netzero.deb).
# Double click on netzero.deb. This pops up the "Open With" command window.
# Copy this command:  dpkg -i %s
# Paste it into the text area of the "Open With" command window.
# Click OK.

This doesnt work in Ubuntu.

After installing using dpkg.  It installs in th opt directory.

What should I run to install this software?

jeff@ubuntu:/opt/nzclient$ ls
accel.mkr  dialerr.sh    images       NetZeroIni.ctl  runclient.sh
cache      dialjar.jar   lib          nzppp           shellui.obj
cache.obj  emltmplt.dat  mdminit      phn.dat         zcastsu.zip
dat        help          NetZero.ini  pool
jeff@ubuntu:/opt/nzclient$ chmod -x runclient.sh
chmod: changing permissions of `runclient.sh': Operation not permitted
jeff@ubuntu:/opt/nzclient$ chmod -x netzero.ini
chmod: cannot access `netzero.ini': No such file or directory
jeff@ubuntu:/opt/nzclient$ gksudo runclient.sh
jeff@ubuntu:/opt/nzclient$

---

### Post by kidux on 2009-03-05
> **jeff35 said:**
> I have a Netzero. deb file that was designed for Linspire. Could someone help me install it in Ubuntu? This is the instructions from Netzero:

# After downloading the installation file it will have a .deb extension (eg netzero.deb).
# Double click on netzero.deb. This pops up the "Open With" command window.
# Copy this command:  dpkg -i %s
# Paste it into the text area of the "Open With" command window.
# Click OK.

This doesnt work in Ubuntu.

After installing using dpkg.  It installs in th opt directory.

What should I run to install this software?

jeff@ubuntu:/opt/nzclient$ ls
accel.mkr  dialerr.sh    images       NetZeroIni.ctl  runclient.sh
cache      dialjar.jar   lib          nzppp           shellui.obj
cache.obj  emltmplt.dat  mdminit      phn.dat         zcastsu.zip
dat        help          NetZero.ini  pool
jeff@ubuntu:/opt/nzclient$ chmod -x runclient.sh
chmod: changing permissions of `runclient.sh': Operation not permitted
jeff@ubuntu:/opt/nzclient$ chmod -x netzero.ini
chmod: cannot access `netzero.ini': No such file or directory
jeff@ubuntu:/opt/nzclient$ gksudo runclient.sh
jeff@ubuntu:/opt/nzclient$
Use sudo in the chmod command to make it executable, maybe.

---

### Post by jeff35 on 2009-03-05
this is the files in the /opt/nzclient

Copy it to /
eg.
cp netzero.deb /
cd /
ar -xv netzero.deb
gunzip data.tar.gz
tar xvf data.tar
rm data.tar control.tar.gz debian-binary
Install Java VM from here as brassfish advised:
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)
cd /opt/nzclient
./runclient.sh








jeff@ubuntu:/opt/nzclient$ ls
accel.mkr  dialerr.sh    images       NetZeroIni.ctl  runclient.sh
cache      dialjar.jar   lib          nzppp           shellui.obj
cache.obj  emltmplt.dat  mdminit      phn.dat         zcastsu.zip
dat        help          NetZero.ini  pool
jeff@ubuntu:/opt/nzclient$ chmod -x runclient.sh

---

### Post by jeff35 on 2009-03-05
I got ./runclient working, but it cant find jave, how do link with my java directory? my java is located /usr/java/jre1.6.0_12
 ln -s /usr/java/jre1.6.0_12?

would it hurt to install java again in directory?

---

### Post by taurus on 2009-03-05
Try something like

```
sudo ln -s /usr/java/jre1.6.0_12/bin/java /usr/local/bin/java
java -version
```

---

### Post by jeff35 on 2009-03-06
Taurus Could you please explain your post better. I tried your command and had no luck. I tried to add java to my path and lost commands. Looks to me like linking ln between ~ and / would be a good way to catch a virus. I liked my 2 jave installation idea. why isn't it working?
jeff@ubuntu:/$ cd /usr/local/bin
jeff@ubuntu:/usr/local/bin$ sudo mkdir java
jeff@ubuntu:/usr/local/bin$ cd java
jeff@ubuntu:/usr/local/bin/java$ sudo mkdir jre1.6.0_12
jeff@ubuntu:/usr/local/bin/java$ cd jre1.6.0_12
jeff@ubuntu:/usr/local/bin/java/jre1.6.0_12$ cd /
jeff@ubuntu:/$  sudo ln -s /user/java/jre1.6.0_12/bin/java /user/local/bin/java/jre1.6.0_12
ln: creating symbolic link `/user/local/bin/java/jre1.6.0_12': No such file or directory



jeff@ubuntu:/$ 
sudo ln -s /usr/java/jre1.6.0_12/bin/java /usr/local/bin/java
java -version

jeff@ubuntu:/opt/nzclient$ ls -l
total 20368
-rwxr-xr-x 1 root root      281 2003-11-14 18:13 accel.mkr
drwxr-xr-x 2 root root     4096 2009-03-04 21:22 cache
-rwxr-xr-x 1 root root   234073 2003-11-12 15:00 cache.obj
drwxr-xr-x 2 root root     4096 2009-03-04 21:22 dat
-rwxr-xr-x 1 root root       56 2003-11-04 13:05 dialerr.sh
-rwxr-xr-x 1 root root     6151 2003-09-26 22:51 dialjar.jar
-rwxr-xr-x 1 root root      468 2003-09-26 22:51 emltmplt.dat
drwxr-xr-x 2 root root     4096 2009-03-04 21:22 help
drwxr-xr-x 6 root root     4096 2009-03-04 21:22 images
drwxr-xr-x 8 root root     4096 2009-03-05 07:05 jre1.6.0_12
-rwx--x--x 1 root root 20168773 2009-03-05 07:01 jre-6u12-linux-i586.bin
drwxr-xr-x 2 root root     4096 2009-03-04 21:22 lib
-rwxr-xr-x 1 root root        9 2003-11-11 09:57 mdminit
-rwxr-xr-x 1 root root       70 2003-11-20 22:09 NetZero.ini
-rwxr-xr-x 1 root root        1 2003-11-12 15:00 NetZeroIni.ctl
-rwxr-xr-x 1 root root    35584 2004-02-24 12:42 nzppp
-rwxr-xr-x 1 root root   219171 2003-09-26 22:51 phn.dat
drwxr-xr-x 2 root root     4096 2009-03-04 21:22 pool
-rwxr-xr-x 1 root root      255 2003-11-14 19:17 runclient.sh
-rwxr-xr-x 1 root root    74283 2003-11-12 15:00 shellui.obj
-rwxr-xr-x 1 root root     7085 2003-11-12 12:47 zcastsu.zip
jeff@ubuntu:/opt/nzclient$ sudo chmod a+x runclient.sh
jeff@ubuntu:/opt/nzclient$ sudo ./runclient.sh
./runclient.sh: 7: java: not found
jeff@ubuntu:/opt/nzclient$

---

### Post by jeff35 on 2009-03-20
update: I would like to thank taurus for his help, our staff.
after install netzero, and java you need to help runclient.sh find java.
gksudo gedit runclient.sh

#!/bin/bash

cd /opt/nzclient

cp=./lib/zcast1_6.jar:./lib/bwt300.jar


/usr/java/jre1.6.0_12/bin/java -cp $cp -Dnz.browser=mozilla -Dnz.clientName=$0 -Dnz.RAS=./nzppp -Dnz.rasdelay=60000 -Dnz.TextFontName=SansSerif -Dnz.TextFontSize=7 -Dnz.FontName=Arial -Dnz.FontSize=9 nzcom.ZCast

---

