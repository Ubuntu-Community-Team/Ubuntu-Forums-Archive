---
title: "warsow: error while loading shared libraries: libcurl.so.3"
date: 2006-07-05
forum: Gaming &amp; Leisure
---

### Post by nickless on 2006-07-05
So I installed Xubuntu and to try if my sound is working fine in games warsow.
Installation under root went smooth, but when I try to launch the game I get this:
```
./warsow-bin: error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory
```

Now I went on doing some research but the only thing I found, ...well looks like a solution alright, but I don't know what the hell I am supposed to do :D

[http://curl.haxx.se/docs/faq.html#5.8](http://curl.haxx.se/docs/faq.html#5.8)

> 5.8 libcurl.so.3: open failed: No such file or directory

This is an error message you might get when you try to run a program linked
with a shared version of libcurl and your run-time linker (ld.so) couldn't
find the shared library named libcurl.so.3.

You need to make sure that ld.so finds libcurl.so.3. You can do that
multiple ways, and it differs somewhat between different operating systems,
but they are usually:

* Add an option to the linker command line that specify the hard-coded path
the run-time linker should check for the lib (usually -R)

* Set an environment variable (LD_LIBRARY_PATH for example) where ld.so
should check for libs

* Adjust the system's config to check for libs in the directory where you've
put the dir (like Linux's /etc/ld.so.conf)

'man ld.so' and 'man ld' will tell you more details 

Hope somebody can translate #-o

---

### Post by DoktorSeven on 2006-07-06
1) make sure libcurl3 is installed (**sudo apt-get install libcurl3**)
2) See if there's a file or link to a file in /usr/lib/ called **libcurl.so.3**; if not, but there is a file called libcurl.so.3.0.0 (or similar), you can make a link to it:
**sudo ln -s /usr/lib/libcurl.so.3.0.0 /usr/lib/libcurl.so.3**
3) If there is a /usr/lib/libcurl.so.3, try running **sudo ldconfig** (rescans all of the library files).

---

### Post by nickless on 2006-07-06
1) worked :D
It's not like I hadn't thought about this, but I tried to download libcurl.so.3 finding nothing and libcurl* finding too much...
thx :D

---

### Post by High_Yield on 2008-09-03
There used to be THANK YOU links - but I do not see one here.
Regardless thanks bro - big help as autodownload in Open Arena was SLOW until I did sudo apt-get install libcurl3

---

