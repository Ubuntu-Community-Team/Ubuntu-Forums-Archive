---
title: "Apt-get Installation Problem (Solved)"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Ingla on 2005-11-14
Hello.

I posted this question a couple of days ago, but I guess nobody saw it. I do need an answer so I'm asking again.

I want to make Flash movies, so I downloaded f4l (a .deb from Sourceforge).

When trying to install the deb, apt-get said the dependencies were unavailable, so I added the following Debian repositories:

deb [ftp://ftp.us.debian.org/debian](ftp://ftp.us.debian.org/debian) stable main contrib non-free
deb [ftp://non-us.debian.org/debian-non-US](ftp://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free


Then apt-get said it couldn't do it because of conflicts and I should try apt-get -f install.

That brought me this:
--------------------------------------------------------------------------
[COLOR="Red"]sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
libqt3c102-mt
Suggested packages:
libqt3c102-mt-psql libqt3c102-mt-mysql libqt3c102-mt-odbc
The following packages will be REMOVED:
f4l k3blibs kdebase-bin kdelibs-bin kdelibs4-dev kdelibs4c2 libarts1-dev
libarts1c2 libdbus-qt-1-1c2 libqt3-mt libqt3-mt-dev licq licq-plugin-qt
qt3-dev-tools
The following NEW packages will be installed:
libqt3c102-mt
0 upgraded, 1 newly installed, 14 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 3045kB of archives.
After unpacking 61.4MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.[/COLOR]
--------------------------------------------------------------------------
As you can see I aborted the operation pending advice because it looks like apt-get wants to remove half the system in order to install this one program.
Aren't these things needed for other apps? Would I dare let apt-get do this?

Thank you.

---

### Post by matthewv on 2005-11-14
Were you trying to install the .deb with apt-get. Wouldnt you do ```
sudo dpkg -i <packagename.deb>
```

---

### Post by arnieboy on 2005-11-14
[QUOTE=Ingla]Hello.

I posted this question a couple of days ago, but I guess nobody saw it. I do need an answer so I'm asking again.

I want to make Flash movies, so I downloaded f4l (a .deb from Sourceforge).

When trying to install the deb, apt-get said the dependencies were unavailable, so I added the following Debian repositories:

deb [ftp://ftp.us.debian.org/debian](ftp://ftp.us.debian.org/debian) stable main contrib non-free
deb [ftp://non-us.debian.org/debian-non-US](ftp://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free


Then apt-get said it couldn't do it because of conflicts and I should try apt-get -f install.

That brought me this:
--------------------------------------------------------------------------
[COLOR="Red"]sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
libqt3c102-mt
Suggested packages:
libqt3c102-mt-psql libqt3c102-mt-mysql libqt3c102-mt-odbc
The following packages will be REMOVED:
f4l k3blibs kdebase-bin kdelibs-bin kdelibs4-dev kdelibs4c2 libarts1-dev
libarts1c2 libdbus-qt-1-1c2 libqt3-mt libqt3-mt-dev licq licq-plugin-qt
qt3-dev-tools
The following NEW packages will be installed:
libqt3c102-mt
0 upgraded, 1 newly installed, 14 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 3045kB of archives.
After unpacking 61.4MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.[/COLOR]
--------------------------------------------------------------------------
As you can see I aborted the operation pending advice because it looks like apt-get wants to remove half the system in order to install this one program.
Aren't these things needed for other apps? Would I dare let apt-get do this?

Thank you.[/QUOTE]
please dont do this again. the repositories u tried to use are debian repos and they WILL make your ubuntu system crash by installing ubuntu incompatible packages.
please remove the repos that u added, do a ```
sudo apt-get update
``` and then do a ```
sudo dpkg -i <packagename>
```
and then paste the terminal output here.

---

### Post by Ingla on 2005-11-15
Hi. 

Did it and here's the output (same as I got originally):
------------------------------------------------------------------
[COLOR="Red"]sudo dpkg -i Desktop/f4l_0-1.2-1_i386.deb
Selecting previously deselected package f4l.
(Reading database ... 98560 files and directories currently installed.)
Unpacking f4l (from Desktop/f4l_0-1.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of f4l:
 f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libxrender1 (>= 1:0.9.0-2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing f4l (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 f4l[/COLOR]
-------------------------------------------------------------------------
So, I tried to get libqt3c102-mt and got this:
-------------------------------------------------------------------------  
[COLOR="Red"]sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate[/COLOR]
--------------------------------------------------------------------------
That's why I tried the Debian repostories.

Now, I tried to get the other dependency and got this:
--------------------------------------------------------------------------
 [COLOR="Red"]sudo apt-get install  libxrender1
Reading package lists... Done
Building dependency tree... Done
libxrender1 is already the newest version.**
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  f4l: Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
       Depends: libqt3c102-mt (>= 3:3.3.4-3) but it is not installable
       Depends: libxrender1 (>= 1:0.9.0-2) but 1:0.9.0-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/COLOR]** I guess that means the newest version available from the Ubuntu repositories?
--------------------------------------------------------------------------
So, I did the "force", and got the following:
--------------------------------------------------------------------------
 [COLOR="Red"]sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  f4l
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1704kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 98563 files and directories currently installed.)
Removing f4l ...[/COLOR]
--------------------------------------------------------------------------
I assume apt-get removed f4l to correct a broken package situation.

Anyway, that's everything I know how to do.

Any ideas?

Thanks.

---

### Post by matthewv on 2005-11-15
Have you got the extra repos enabled???

---

### Post by Ingla on 2005-11-15
I disabled the Debian ones I mentioned originally.

The only extra ones I have are:

deb [http://debian-hebrew.alioth.debian.org/debian/](http://debian-hebrew.alioth.debian.org/debian/) stable main
deb-src [http://debian-hebrew.alioth.debian.org/debian/](http://debian-hebrew.alioth.debian.org/debian/) stable main

which were for language support (which I have now). They've been enabled for a long time without causing any problems.

---

### Post by Hallavej on 2005-11-15
Did you try:
sudo apt-get install libqt3-mt
and then install your .deb file. And if it does not work try:
dpkg --force-<something> the_file.deb
with <something> replaced by... well I dont know, see:
dpkg --force-help
for options

libqt3c102-mt has been replaced by libqt3-mt, so I guees they must be almost the same thing.

---

### Post by rejser on 2005-11-16
I've been trying the same thing.
I get 
[COLOR="Red"]rejser@LaQuisha:~/Desktop$ sudo dpkg -i f4l_0.2-1_i386.deb
V&#228;ljer tidigare ej valt paket f4l.
(L&#228;ser databasen ... 58206 filer och kataloger installerade.)
Packar upp f4l (fr&#229;n f4l_0.2-1_i386.deb) ...
dpkg: beroendeproblem f&#246;rhindrar konfigurering av f4l:
 f4l beror p&#229; libqt3c102-mt (>= 3:3.3.4), men:
  Paket libqt3c102-mt &#228;r ej installerat.
 f4l beror p&#229; libqt3c102-mt (>= 3:3.3.4-3), men:
  Paket libqt3c102-mt &#228;r ej installerat.
 f4l beror p&#229; libxrender1 (>= 1:0.9.0-2), men:
  Versionen av libxrender1 p&#229; systemet &#228;r 1:0.9.0-1.
dpkg: fel vid hantering av f4l (--install):
 beroendeproblem - l&#228;mnar okonfigurerad
[/COLOR]
Can't find where libxrender1, otherwise maybe I could "ln -s" it (make a symlink)
ed: did install libqt3-mt

---

### Post by Yagisan on 2005-11-16
Please follow these instructions to add universe and multiverse [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) then try again and post your results

---

### Post by rejser on 2005-11-16
the same, already had them

---

### Post by rejser on 2005-11-20
Solved it.
did mkdir f4l && dpkg-deb -x f4l****.deb f4l/
then I could run it from f4l/usr/bin/ with ./f4l
so I copied the f4l file in f4l/usr/bin/ to /usr/bin and voila!
it didn't care about the libqt3c102-mt or libqt3-mt

---

### Post by Ingla on 2005-11-21
Wow! That's fantastic! How did you think of that??

I did it, and then added it to the Applications>Graphics menu with the Menu Editor (Name: f4l, Command: /usr/bin/f4l). Now I can just run it from the menu.

Question 1: I don't know how to use Flash, but am planning to learn. Meanwhile, have you tried it out? Does it work (without the dependencies)?

Question 2: Have you tried this installation method before? Will it work with other programs that have dependency problems?

If so, you should post a How-To.

Please let me know.

Thanks.

---

### Post by nevernamed on 2007-03-14
lol.... dumb question, but I've been looking everywhere and I can't find the f4l debian package. Can you point me in the right direction?
Thanks.

---

### Post by philpinch on 2007-05-02
you can download the RPM package at the following URL : 
[http://rpm.pbone.net/index.php3?stat=3&search=f4l&srodzaj=3]("http://rpm.pbone.net/index.php3?stat=3&search=f4l&srodzaj=3")
. Then, use the Alien tools to convert package RPM to DEB. ([http://doc.ubuntu-fr.org/alien]("http://doc.ubuntu-fr.org/alien"))

---

