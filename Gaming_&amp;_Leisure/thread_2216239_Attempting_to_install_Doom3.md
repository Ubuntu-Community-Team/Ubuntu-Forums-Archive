---
title: "Attempting to install Doom3"
date: 2014-04-10
forum: Gaming &amp; Leisure
---

### Post by Comicalizard on 2014-04-10
Hey guys I am attempting to install Doom3 and have copied all pak files into their directory. I am not trying to start the game and get this...

kris@kris-VPCCW17FX:~$ doom3
./doom.x86: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
kris@kris-VPCCW17FX:~$ 

What does that mean?

FYI just got Ubuntu so I am pretty ignorant, still learning!  :confused:

---

### Post by Toz on 2014-04-10
Hello and welcome to the forums.

The message means that either the libX11.so.6 file doesn't exist on your system or can't be found by the doom executable. libX11.so.6 is part of the **libx11-6** package. To check if its installed, run the following command in a terminal window:
```
apt-cache policy libx11-6
```

If its not installed, you can install the package by:
```
sudo apt-get install libx11-6
```
...and enter your password when prompted (sorry about all the command line).

If the package is installed, we'll need to see why it can't find the file.

By the way, which version of Ubuntu did you install?

---

### Post by Comicalizard on 2014-04-10
12.04, and thank you so much! I'll check it out right now!

---

### Post by efflandt on 2014-04-10
Are you running 32-bit or 64-bit 12.04? If you are running 64-bit you likely need to install ia32-libs to get 32-bit libs, since doom.x86 is 32-bit.

Newer 64-bit Ubuntu versions have some (but not necessarily all) 32-bit libs installed by default.

---

### Post by Comicalizard on 2014-04-10
It is 64 bit, I'll check that out as well. As for the libx11 file I do have that.

libx11-6:
  Installed: 2:1.4.99.1-0ubuntu2.2
  Candidate: 2:1.4.99.1-0ubuntu2.2
  Version table:
 *** 2:1.4.99.1-0ubuntu2.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.4.99.1-0ubuntu2.1 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
     2:1.4.99.1-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages

---

### Post by Comicalizard on 2014-04-10
Thank you guys so much! I am now able to start an play Doom 3! :guitar:

@efflandt You were definitely right I needed to install the 32 bit libs.

See you guys on the front lines!

---

### Post by Toz on 2014-04-10
@efflandt is right, you'll need to install the 32-bit libraries.

---

