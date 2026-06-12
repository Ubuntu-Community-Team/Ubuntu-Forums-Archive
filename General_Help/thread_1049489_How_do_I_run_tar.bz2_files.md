---
title: "How do I run tar.bz2 files?"
date: 2009-01-24
forum: General Help
---

### Post by Dustin2128 on 2009-01-24
I just downloaded google desktop, and it came as a tar.bz2 file extension. How would I run it, could I run it like a .deb package from the terminal?

---

### Post by Dustin2128 on 2009-01-24
google gadgets, not google desktop

---

### Post by bgerlich on 2009-01-24
You don't run them, those are archives. If you don't know what to do with them - better steer clear. The files you are searching for end with .deb - those are Ubuntu software packages. Good site to get them (other than using Add/Remove Programs) is [http://www.getdeb.net/](http://www.getdeb.net/)

If you want to install google gadgets check out this tutorial with direct link to the google gadgets .deb package on getdeb:

[http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-810-intrepid-ibex.html)

---

### Post by xc1024 on 2009-01-24
tar.bz2 are archives. usually they contain source of application. you have to compile it. i googled a nice universal tutorial for most apps, but i can't find it in bookmarks.

---

### Post by mb_webguy on 2009-01-24
As everyone else has said, tar.bz files are archives, sort of like zip files.  They usually contain source code for compiling software on Linux, but just like a zip file they can contain any collection of files.  You may also see other tar files (commonly called "tarballs", since the purpose of tar is to combine multiple files into a single file for archiving), which have other extensions such as gz, bz2, or lz, which simply use a different form of compression.  All of these can be opened using Archive Manager (File Roller), or with the "tar" command in the terminal.

You can find more information about archives on [this page]("https://help.ubuntu.com/community/FileCompression").  If you want to learn how to compile source code, read [this page]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by jespdj on 2009-01-24
You can unpack a .tar.bz2 file with a command like this:
```
tar xvfj filename.tar.bz2
```

---

### Post by Hollyecho_Montgomery on 2011-03-03
I need to know what I am missing.  I am trying to install yaWP.

This is what I got as a message:

hollyecho@Presario-F500-GF596UA-ABA:~$ sudo aptitude install build-essential
[sudo] password for hollyecho: 
sudo: aptitude: command not found
hollyecho@Presario-F500-GF596UA-ABA:~$ cd Downloads
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads$ bunzip2 yawp-0.3.6.tar.bz2
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads$ tar xf yawp-0.3.6.tar
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads$ cd yawp-0.3.6
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads/yawp-0.3.6$ ./configure
bash: ./configure: No such file or directory
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads/yawp-0.3.6$ ./install.sh
DEBUG: -DCMAKE_BUILD_TYPE=Release
UNITTESTS: 
LOGLEVEL: -DDEBUG_LOGLEVEL=Debug
LOGFILE: -DDEBUG_LOGFILE=/tmp/yawp.log
./install.sh: line 209: cmake: command not found
**[COLOR=Red]CMake failed. Your system probably does not meets all requirements.[/COLOR]**
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads/yawp-0.3.6$ 

How can I solve this?  Its a weather program, I replaced my Win7Ulti for Kubuntu 10.10, I had 1st installed Ubuntu 10.10, and thought this might (Kubuntu) might be an easier trans, but, I have lots of problems installing anything else but straight .deb files.  

Help please??

---

### Post by gandaran on 2011-03-03
Hollyecho_Montgomery
> hollyecho@Presario-F500-GF596UA-ABA:~$ sudo aptitude install build-essential
[sudo] password for hollyecho: 
sudo: aptitude: command not found
try
```
sudo apt-get install build-essential
```

---

### Post by Hollyecho_Montgomery on 2011-03-09
> **gandaran said:**
> Hollyecho_Montgomery

try
```
sudo apt-get install build-essential
```


Thank you ever so much.  I never got an email saying anything that there was a reply or addition to this post.):P

---

