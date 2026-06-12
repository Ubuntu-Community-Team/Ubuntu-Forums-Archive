---
title: "Error installing awn-core-applets"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by Odin2347 on 2008-02-02
Well I tried to install the core applets after installing avant and I get this error ```
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr151-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking python-libawn-bzr (from .../python-libawn-bzr_0.2.0-bzr151-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr151-1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package python-libawn0
Selecting previously deselected package awn-core-applets-bzr.
Unpacking awn-core-applets-bzr (from .../awn-core-applets-bzr_0.2.0-bzr248-1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_amd64.deb
 /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr151-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
odin@odin-desktop:~$ 

```

Any suggestions?

---

### Post by sboysel on 2008-02-06
I have the same problem:
```

dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr155-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr155-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by hunter_te on 2008-02-10
Exactly same problem for me too


```

sudo apt-get install avant-window-navigator-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed:
  avant-window-navigator-bzr libawn-bzr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/368kB of archives.
After unpacking 1634kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 92455 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr155-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr155-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Unpacking avant-window-navigator-bzr (from .../avant-window-navigator-bzr_0.2.0-bzr155-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/avant-window-navigator-bzr_0.2.0-bzr155-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/avant-window-navigator/defs/awn.defs', which is also in package python-libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr155-1_i386.deb
 /var/cache/apt/archives/avant-window-navigator-bzr_0.2.0-bzr155-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by hunter_te on 2008-02-12
BUMP....

Please Help. My System is fully up-to-date. I have checked many times now with even all repos enabled. Where is the problem??

---

### Post by hunter_te on 2008-02-15
Three people have same problem, but no-one gives a damn??

BUMP !!!!!!

---

### Post by SomeGuyDude on 2008-02-15
Did you install AWN from the repos? If so, there's your conflict. They don't play nice with one another. You'll have to do a complete removal of, I believe, python-awn, libawn0, awn-manager, and avant-window-navigator as they came in the repos.

Then follow the instructions in the thread here on UF. I have no idea what's up with the repos and why it conflicts with the version on here, but the only way I got the applets was to remove everything that came in the repos automagically and install purely via the instructions here.

Sorry if my language is muddled, it's after 3am and I'm on my way to bed.

---

### Post by eeclark on 2008-02-17
no core applets for the awn version in the ubuntu repos.
if you want / need the core applets (as most do) the only way is to use the bzr version of awn (and remove the other version).

---

### Post by SomeGuyDude on 2008-02-17
> **eeclark said:**
> no core applets for the awn version in the ubuntu repos.
if you want / need the core applets (as most do) the only way is to use the bzr version of awn (and remove the other version).

That's what I meant. If you try and install the applets via bzr when you have the repos AWN installed, you'll get all kinds of errors.

---

### Post by zyvx on 2008-02-18
So how exactly do we go about doing that (being a complete n00b?) And i'm not really sure wich install guide you are talking about as I saw several.

---

### Post by chavanak on 2008-02-18
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/



This removes awn completely. Then do a fresh installlation

---

### Post by zyvx on 2008-02-18
worked perfectly thank you

---

