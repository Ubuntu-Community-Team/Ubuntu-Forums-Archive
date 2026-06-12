---
title: "&quot;./&quot; command not working"
date: 2009-02-07
forum: General Help
---

### Post by Ubun00btu on 2009-02-07
The title pretty much says it.  Not matter what I try: sudo ./make ./configure ./fimename.bin, I get "command not found".    Could someone provide me with the simple answer I'm missing so I can feel foolish but be able to install things again?

Thanks.

Ubuntu 8.10, (almost fresh install)

---

### Post by taurus on 2009-02-07
./ means current directory so unless you are in the right directory, ./ is useless anyway.

Again, make sure you are in the _right directory_, where the program that you want to execute, before you put the ./ in front of a program name.

---

### Post by m_duck on 2009-02-07
The ./ expression is used to execute an executable in the current directory. "make" as a separate command and should work without the "./". As far as ./configure goes, ensure that there is a configure script and check that you are in the directory where the "configure" script is.

---

### Post by Ubun00btu on 2009-02-08
OK, thanks for making that distinction for me about the directory and command.  

The problem it would seem is that the *commands* aren't working.  Make, configure, etc...  I downloaded a .tar.gz, did the usual unpacking (tar -modifier filein.tar.gz fileout.tar.gz) and made sure I was in the proper directory and tried configure and make... neither worked.

---

### Post by taurus on 2009-02-08
> **Ubun00btu said:**
> OK, thanks for making that distinction for me about the directory and command.  

The problem it would seem is that the *commands* aren't working.  Make, configure, etc...  I downloaded a .tar.gz, did the usual unpacking (tar -modifier filein.tar.gz fileout.tar.gz) and made sure I was in the proper directory and tried configure and make... neither worked.

Not every .tar.gz requires you run ./configure && make && sudo make install.  You need to look at either the readme.txt (Readme.txt/README.txt) or the INSTALL for more info.  Otherwise, change to whichever directory you just unpacked and post the output of this command.

```
ls -la
```

---

### Post by Ubun00btu on 2009-02-14
Sorry it took so long to reply, I'd already deleted the directory and files I couldn't install.  I tried this program the other day and here's the results:

Still getting command not found.

```
drwxr-xr-x  3 jeff jeff   4096 2009-02-14 10:11 .
drwxr-xr-x 44 jeff jeff   4096 2009-02-14 10:11 ..
-rw-r--r--  1 jeff jeff   2456 2009-02-14 10:11 config
-rw-r--r--  1 jeff jeff   2456 2009-02-14 10:11 config.default
-rw-r--r--  1 jeff jeff   7652 2009-02-14 10:11 daemon.py
-rw-r--r--  1 jeff jeff   3730 2009-02-14 10:11 installer.py
-rw-r--r--  1 jeff jeff   8077 2009-02-14 10:11 performance.png
-rw-r--r--  1 jeff jeff   7879 2009-02-14 10:11 power_saving.png
-rw-r--r--  1 jeff jeff   9376 2009-02-14 10:11 stock.png
drwxr-xr-x  6 jeff jeff   4096 2009-02-14 10:11 .svn
-rw-r--r--  1 jeff jeff   2441 2009-02-14 10:11 wattospm-daemon
-rw-r--r--  1 jeff jeff  21068 2009-02-14 10:11 wattospm-daemon.py
-rw-r--r--  1 jeff jeff 123929 2009-02-14 10:11 wattospm.glade
-rwxr-xr-x  1 jeff jeff  34835 2009-02-14 10:11 wattospm.py

```

---

### Post by geirha on 2009-02-14
Well, there's no configure script there, so that's why ./configure won't work. Unfortunately there's not README file either, it's common to provide some documentation as to how to install things. 

I recommend you search the site where you got the tar.gz from and look for instructions on how to install and use it.

---

### Post by m_duck on 2009-02-14
I would advise what geirha said, but looking at the files there it'll probably be something like, cd to the directory then in terminal```
python installer.py
```But like I said, best checking first.

---

### Post by Ubun00btu on 2009-02-14
OK thanks,  that isn't the app I was trying to install initially that gave me the error.  I'll see if I can locate an app that I want to install (I think I was trying to build an installation of Sketchup) and try to reproduce the problem.

BTW the app in the above code installed fine using python.

---

