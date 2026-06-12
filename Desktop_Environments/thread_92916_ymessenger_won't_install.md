---
title: "ymessenger won't install"
date: 2005-11-20
forum: Desktop Environments
---

### Post by montes.c on 2005-11-20
xochiyotl# dpkg -i ymessenger_1.0.4_1_i386.deb 
(Reading database ... 73094 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger



I am trying to install the unix yahoo messenger from [http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)

Now I am having problems, I know Perl is already installed but I ran a test and see what happens here:

xochiyotl# apt-get install perl
Reading package lists... Done
Building dependency tree... Done
perl is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ymessenger: Depends: libgdk-pixbuf2 (>= 0.13.0) but it is not going to be installed
              Depends: libssl0.9.6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by RAOF on 2005-11-20
Well, you could use apt-get to install those dependencies, like so:
```
sudo apt-get install libgdk-pixbuf2 libssl0.9.6
```
and then sudo dpkg -i ...

Edit: Have you tried running sudo apt-get -f install, as it suggests?

---

### Post by montes.c on 2005-11-20
Yes I did, but now there was an update marker on my gnome desktop, I ran it and it fixed it..... ymessenger now works, thanks.

---

### Post by lo900 on 2006-11-10
I have the same errors, so I try to install it manually (my way)

I have un pack it , I found inside it 2 gz files, unpacking the one with "data.tar.gz", I've found in it folder /./opt/ymessenger/
so I put it in /opt, so now I have /opt/ymessenger/ with 2 folder in it
inside /opt/ymessenger/bin/ I found "ymessenger" I ran it,

guess what, it worked.

this is not howto, it worked by luck only

good luck

Lo900

ubuntu Dapper

---

