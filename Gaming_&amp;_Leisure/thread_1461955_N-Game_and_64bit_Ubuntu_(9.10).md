---
title: "N-Game and 64bit Ubuntu (9.10)"
date: 2010-04-24
forum: Gaming &amp; Leisure
---

### Post by brandon89 on 2010-04-24
hey guys, so im trying to run N-game ([http://www.thewayoftheninja.org/n_downloads.html](http://www.thewayoftheninja.org/n_downloads.html)) but whenever i try to run it, i get this error

> ~/Downloads/n_v1linux$ ./n_v14
./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


so then i tried to download libgtk1.2 but i then get this

> ~/Downloads/n_v1linux$ sudo aptitude install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for libgtk1.2
No candidate version found for libgtk1.2
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


so how would i go about installing libgtk1.2?  thanks for any help

---

### Post by kiddykoff on 2010-04-25
i'm getting problems too, but when i run

```
kurtis@ubuntu:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtk1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk1.2 has no installation candidate

```

I'm really tired, so i'll check on this later

---

### Post by Perfect Storm on 2010-04-25
libgtk1.2 is obsolite, you can get the package here; [http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all)

---

### Post by kiddykoff on 2010-04-25
Theres not very much documentation for this game. even the readme file is limited in the amount instruction given. It may be easier to just get this going in WINE.

I installed those packages and i still get the same error message. even with the dependencies installed.

---

### Post by brandon89 on 2010-04-26
yeah i get the same errors messages as well.  however, i did try extracting the libgtk1.2.so.0 file (32 bit) into my usr/lib32 folder and now i get this error instead:

> ./n_v14: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory


i tried looking at the website posted earlier for the file but i couldnt find it.  i think i may just keep doing this until it runs haha.  any help on finding this package though?

---

### Post by Perfect Storm on 2010-04-26
If N-Game is 32-bit you need to install the dependenies with 32-bit libs.
The easist way is to use getlibs for that purpose;

```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
getlibs --help
```


[

---

### Post by brandon89 on 2010-04-26
ok, however, when i use that i get this

> ~/Downloads/n_v1linux$ getlibs ./n_v14
libgmodule-1.2.so.0: libglib1.2
No match for libglib-1.2.so.0
No match for libstdc++-libc6.2-2.so.3
libgmodule-1.2.so.0: libglib1.2
No match for libglib-1.2.so.0
libgmodule-1.2.so.0: libglib1.2
No match for libglib-1.2.so.0
The following i386 packages will be installed:
libglib1.2
Continue [Y/n]? y
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install


what repository would i need to enable/add?  sorry for all the questions

---

### Post by Perfect Storm on 2010-04-26
As said before libgtk1.2 (and some of its dependenies) are obsolite, therefore download libgtk1.2 and libglib1.2 32-bit to your HDD.

Then you can use getlibs to install them.

```
getlibs -i libgtk1.2_1.2.10-18.1build2_i386.deb
getlibs -i libglib1.2-dbg_1.2.10-19build1_i386.deb
```

---

### Post by 3rdalbum on 2010-04-26
The Windows version of N works in Wine, if you can't get the native one working.

---

### Post by Bad_Andy on 2010-04-26
i installed getlibs and tried what the previous poster said but i get this:

> leecarey@leecarey-desktop:~$ getlibs -i libgtk1.2_1.2.10-18.1build2_i386.deb

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk1.2_1.2.10-18.1build2_i386.deb
leecarey@leecarey-desktop:~$ 
leecarey@leecarey-desktop:~$ getlibs -i libglib1.2-dbg_1.2.10-19build1_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglib1.2-dbg_1.2.10-19build1_i386.deb
leecarey@leecarey-desktop:~$ 


---

### Post by Perfect Storm on 2010-04-26
write **getlibs -i** then drag the package into the terminal. It's properly that the package is in a different directory or the name of the package is a bit different.

---

