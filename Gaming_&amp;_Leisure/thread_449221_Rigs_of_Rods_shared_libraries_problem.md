---
title: "Rigs of Rods shared libraries problem"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by Christopherius on 2007-05-20
I got this error after trying to run RoRconfig:

./RoRconfig.bin: error while loading shared libraries: libwx_gtk2_xrc-2.6.so.0: cannot open shared object file: No such file or directory

I have libwx_gtk2 installed so I'm not sure what the problem is. This game looks really cool I'd like to get it
running soon.

Thanks in advance for any help

---

### Post by joshuapurcell on 2007-05-20
Although not with this game, I'm having a similar problem. I'm trying to run the LGP_Uninstall program and it keeps giving this error:```
joshua@desktop:~$ lgp_uninstall 
lgp_uninstall: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```But the file it's complaining about is located in the /usr/lib directory:```
joshua@desktop:/usr/lib$ ls -l libgtk-1.2.so.0
lrwxrwxrwx 1 root root 19 2007-03-26 21:14 libgtk-1.2.so.0 -> libgtk-1.2.so.0.9.1
```I've tried running lgp_uninstall from the /usr/lib directory but that didn't help. lgp_update runs without problems.

---

### Post by joshuapurcell on 2007-05-20
If I set LD_LIBRARY_PATH, my error changes to the following:```
joshua@desktop:/usr/lib$ export LD_LIBRARY_PATH=/usr/lib
joshua@desktop:/usr/lib$ lgp_uninstall 
lgp_uninstall: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64
```From here I should be able to download the 32-bit version of libgtk-1.2, but packages.ubuntu.com is down at the moment.

Anyone know what is wrong with [https://packages.ubuntu.com/feisty/](https://packages.ubuntu.com/feisty/) ?

EDIT: I've extracted the libraries from the debian packages **libglib1.2_1.2.10-17build1_i386.deb** and **libgtk1.2_1.2.10-18_i386.deb** into /usr/lib32, and then lgp_uninstall worked. I still don't know what's wrong with the above URL though.

---

### Post by rcatman on 2007-06-18
it is [http://packages.ubuntu.com](http://packages.ubuntu.com)

not http**s**://packages.ubuntu.com

I'm trying to solve this shared library problem as well.

---

### Post by rcatman on 2007-06-18
So far I've fixed some 'loading shared libraries' errors. I've had to download a lot of RPM files and convert them to deb packages. Also I had to symlink libtiff4 to libtiff3. Anywho, I'm still fixing the "wxWidgets for GTK (wxgtk) version 2.6" dependencies from the README.LINUX txt file. 

RoR requires certain versions that aren't in the ubuntu package repositories. My guess is RoR hasn't been updated recently enough.

---

### Post by rcatman on 2007-06-19
So I'm giving up. 

I've discovered the problems I've been experiencing is due to not having the non-unicode version of wxGTK. 

The author posted that he would include those files into the next release. Guess I'll just have to wait unless anyone knows where I can download it.

---

### Post by rcatman on 2007-06-21
I found a solution.

goto [www.wxwidgets.com](www.wxwidgets.com), download the 2.6.x version, compile and copy the files from the new lib folder into your /usr/lib folder.

---

### Post by Cappy on 2007-06-21
Next time you have a library problem you should try my program getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

