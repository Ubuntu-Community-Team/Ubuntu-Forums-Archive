---
title: "install digital library"
date: 2009-02-12
forum: Education &amp; Science
---

### Post by blackcloud on 2009-02-12
i want install in my ubuntu 8.04 server greenstone for making digital library but always failed anybody knows how to install it, i try install from greenstone.bin, svn, binnary but the result still failed. help me pls.

---

### Post by cariboo on 2009-02-12
Open a Applications-->Accessories-->Terminal and cd to the directory where the file  is located. For this example I'll assume the file is on the desktop:

```
cd ~/desktop
```

the next thing to do is to make the file executable:

```
chmod +x Greenstone-2.81-linux.bin
```

next install the program:

```
sudo ./Greenstone-2.81-linux.bin
```

The above command will install Greenstone, from there refer to [the installation manual]("http://www.greenstone.org/manuals/gsdl2/en/html/Chapter_installation_procedure.htm#Section_unix") to finish setting Greenstone up.

Jim

---

### Post by blackcloud on 2009-02-12
i am not succes to install greenstone,this happen to my ubuntu server :
This application requires a Java Run Time Environment (JRE)to run. Searching for one on your computer was not successful.Please use the command line switch -is:javahome to specifya valid JRE.  For more help use the option -is:help.

and i has install java this is mine 
root@server:/home/clarck# java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing.

how i can solved my problem ?

---

### Post by sharon.gmc on 2009-02-13
We have used the GSDL software from UW in NZ under windows but it was orginally developed for Linux and then ported so we wanted to try it out on Ubuntu. The longer term goal is to then use the server install with the Ubuntu server machine so that it can do OAI and Z39.50 harvesting.

Anyway Greenstone has some dependencies, you need a JVM and the ImageMagick image processing utilities. We had installed Java a long time ago so all we needed to do is to run the package manager an install imagemagick.

Next it is off to the Greenstone home page at [http://www.greenstone.org/download](http://www.greenstone.org/download) to get gsdl-2.80-unix.tar.gz and to open it with the archive manager. We drag the gsdl-2.80-unix folder to our home directory and take a look at the readme file. The home page says:

To install this distribution, extract the gzipped tar archive and run the setupLinux.bin Java-based Installer program. Alternatively, run the Install.sh shell script from within the gsdl-X.XX-unix/Unix directory (see the Installer's Guide for more detailed installation instructions).

---

### Post by blackcloud on 2009-02-15
thanks iam succes installing greenstone in my ubuntu server. iam install from binaris. thank you very much.

---

### Post by blackcloud on 2009-02-23
i has been installing greenstone on my ubuntu server and i installing gli client and its work. but i found some error when i making some collection book and open it i found that my greenstone can't load text and in my log i found this 
"Warning: redefinition of _help:texthelpquerytermstitle_[l=fr] on line 607 of /var/www/gsdl/macros/french.d" 
how i can solve this

---

