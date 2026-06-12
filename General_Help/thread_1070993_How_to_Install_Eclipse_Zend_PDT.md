---
title: "How to Install Eclipse Zend PDT?"
date: 2009-02-15
forum: General Help
---

### Post by esender on 2009-02-15
Hey Everyone,

I am new to linux and I am also tired of using XAMPP on my windows machine. It crashes every 2 seconds.

So I decided to take the leap into Linux and chose Ubuntu 8.10 64bit and I am using VirtualBox.

Anyway, on to my question:

I would like to set up Eclipse's Zend PDT application. This is different from regular Eclipse that you can download with the Synaptic service (I can't find it on there or on the Add/Remove thing)

The link for it is here:
[http://www.zend.com/en/community/pdt](http://www.zend.com/en/community/pdt)
or here to download: [http://downloads.zend.com/pdt/all-in-one/pdt-2.0.0GA_debugger-5.2.15.v20081217-all-in-one-linux-gtk.tar.gz](http://downloads.zend.com/pdt/all-in-one/pdt-2.0.0GA_debugger-5.2.15.v20081217-all-in-one-linux-gtk.tar.gz)

I am used to Window's and the ability to double click on a new executable and use it. Zend/Eclipse on Windows is just a simple double click. That is, you download the archived file, decompress it, and double click on eclipse.exe.

I really cannot figure out how to execute the Eclipse Zend for linux.

Any help would be very appreciate... thanks!

---

### Post by esender on 2009-02-15
I wanted to mention, I did download the .tar.gz file containing the Eclipse set up. I then tried the "./eclipse" command to start it and it didn't work. See this:

```
eric@Eric-linux:~/Desktop/eclipse$ ls -la
total 460
drwxrwxr-x  9 eric eric   4096 2008-12-29 05:29 .
drwxr-xr-x  3 eric eric   4096 2009-02-15 17:11 ..
drwxr-xr-x  2 eric eric   4096 2008-09-11 16:37 about_files
-rwxr-xr-x  1 eric eric  13852 2008-09-11 16:24 about.html
-rw-rw-r--  1 eric eric  39292 2008-09-11 16:37 artifacts.xml
drwxr-xr-x  5 eric eric   4096 2008-09-11 16:37 configuration
drwxrwxr-x  3 eric eric   4096 2008-12-29 03:22 dropins
-rwxr-xr-x  1 eric eric  52576 2008-09-11 16:24 eclipse
-rwxr-xr-x  1 eric eric    161 2008-09-11 16:37 eclipse.ini
-rwxr-xr-x  1 eric eric     59 2008-09-11 16:24 .eclipseproduct
-rwxr-xr-x  1 eric eric  16536 2008-09-11 16:24 epl-v10.html
drwxrwxr-x  7 eric eric   4096 2008-12-29 05:29 features
-rwxr-xr-x  1 eric eric 266168 2008-09-11 16:24 libcairo-swt.so
-rwxr-xr-x  1 eric eric   6506 2008-09-11 16:24 notice.html
drwxrwxr-x  5 eric eric   4096 2008-09-11 16:37 p2
drwxrwxr-x 10 eric eric  16384 2008-12-29 05:30 plugins
drwxr-xr-x  2 eric eric   4096 2008-09-11 16:37 readme
eric@Eric-linux:~/Desktop/eclipse$ ./eclipse
bash: ./eclipse: No such file or directory

```

See as you can see, it thinks its not there or something.

---

### Post by shawinder on 2010-11-20
The command ./eclipse works for me.

Make sure that  you have the latest java libraries installed as eclipse needs Java runtime to execute

$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk

---

