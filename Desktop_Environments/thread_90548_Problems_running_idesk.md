---
title: "Problems running idesk"
date: 2005-11-15
forum: Desktop Environments
---

### Post by chem415 on 2005-11-15
Hi, 

Ubuntu 5.04 Installed with HP iso on nc6000 compaq/hp. 

I am trying to use idesk 0.5.5 (installed via apt-get) and I see the following error when starting from the command line, 

Segmentation fault. 

I have one *.lnk file in my ~/.idesktop directory which looks like, 

$cat mutt.lnk 
table Icon
  Caption: E-Mail
  Command: Eterm -fg white -bg black -e mutt
  Icon: /home/marc/idesktop-bkup/xterm.png
  X: 16
  Y: 302
end

I am using the default .ideskrc that is installed in /usr/share/doc/idesk/examples.

I have also tried to compile from source. I get the following error, 

checking for X... no
configure: error: Idesk requires the X Window System libraries and headers.

I am currently in fluxbox, but it appears that idesk is looking for some other X libs, soo my question is, does anyone out there now what packages idesk is looking for? Obviously the X ones, but what specific names ;), since running 

$sudo apt-get install X*

is a bit silly.  I am running gcc 3.3.5. 

Thanks for any help. 

chem415

---

### Post by chem415 on 2005-11-15
ok i just found them :).  Just in case anyone runs in to this problem, the libs which you need are in the following packages

xlibs-dev 6.8.2-10.1.. 

I ran 

Thanks, 

chem415

---

### Post by Xian on 2005-11-26
[QUOTE=chem415]I have also tried to compile from source. I get the following error, 

checking for X... no
configure: error: Idesk requires the X Window System libraries and headers.[/QUOTE]

The idesk program is in the repos and works fine in Ubuntu.

```
$ apt-cache policy idesk
idesk:
  Installed: 0.7.3-2
  Candidate: 0.7.3-2
  Version table:
 *** 0.7.3-2 0
        500 http://archive.ubuntu.com breezy/universe Packages
        100 /var/lib/dpkg/status
```

---

