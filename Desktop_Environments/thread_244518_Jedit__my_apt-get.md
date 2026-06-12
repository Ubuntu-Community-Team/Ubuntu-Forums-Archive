---
title: "Jedit ****** my apt-get"
date: 2006-08-26
forum: Desktop Environments
---

### Post by doomstone on 2006-08-26
I have just tryed to install the jedit .deb pack from their homepage.
[http://www.jedit.org/](http://www.jedit.org/)
But the installed failed. and now when i try to opem my apt-get do i get this message.

Reading package lists... Done
Building dependency tree... Done
E: The package jedit needs to be reinstalled, but I can't find an archive for it.

i have tryed to apt-get remove jedit, but i just get the same message there. How can i fix this?

---

### Post by christhemonkey on 2006-08-26
Did you try and redownload the .deb archive and then installing it again?

```
sudo dpkg -i jedit-bla-version-whatever.deb
```


And if that doesnt work,
```
sudo apt-get install -f 
```
Should fix any borken packages you have lying around.

---

### Post by doomstone on 2006-08-26
When i try to reinstall
> doomstone@doomtop:~$ sudo dpkg -i Desktop/jedit_4.3pre6_all.deb
dpkg-deb: unexpected end of file in version number in Desktop/jedit_4.3pre6_all.deb
dpkg: error processing Desktop/jedit_4.3pre6_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 Desktop/jedit_4.3pre6_all.deb
doomstone@doomtop:~$


And  sudo apt-get install -f
> doomstone@doomtop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
E: The package jedit needs to be reinstalled, but I can't find an archive for it.


---

### Post by Ramses de Norre on 2006-08-26
I guess there is a problem with the .deb.. Try ```
sudo dpkg -r jedit_*_all.deb
sudo apt-get install -f
```
And search for another .deb.

---

### Post by doomstone on 2006-08-26
> **Ramses de Norre said:**
> I guess there is a problem with the .deb.. Try ```
sudo dpkg -r jedit_*_all.deb
sudo apt-get install -f
```
And search for another .deb.

doomstone@doomtop:~/Desktop$ sudo dpkg -r jedit_*_all.deb
Password:
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

doomstone@doomtop:~/Desktop$ sudo dpkg -r jedit
dpkg: error processing jedit (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 jedit
doomstone@doomtop:~/Desktop$

---

### Post by Crooksey on 2006-08-26
```

sudo apt-get update

sudo apt-cache search jedit

```

See what related packages there are.

---

### Post by gruffy-06 on 2006-08-26
Is there an apt repository for Jedit? If not add the following to /etc/apt/sources.list:

deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./

Run *apt-get update*, then install necessary packages.

---

### Post by jimmygoon on 2006-08-26
1. Do you have the whole apt-get thing worked out now? If so, then stop downloading the deb... add the sf.net repo's to your sources.list and apt-get install jedit...

---

### Post by cstudent on 2006-08-26
Another thread that may be of help to you:

[http://www.ubuntuforums.org/showthread.php?t=243259](http://www.ubuntuforums.org/showthread.php?t=243259)

---

### Post by doomstone on 2006-08-27
doomstone@doomstone:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 74B in 0s (97B/s)
Reading package lists... Done
doomstone@doomstone:~$ sudo apt-cache search jedit
jedit -

---

