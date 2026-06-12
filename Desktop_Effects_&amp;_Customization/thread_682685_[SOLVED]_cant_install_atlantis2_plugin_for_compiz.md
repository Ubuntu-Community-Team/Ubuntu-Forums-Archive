---
title: "[SOLVED] cant install atlantis2 plugin for compiz"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by adz666 on 2008-01-30
i need help installing this. ive looked ato other threads but they dont seem to help.

can someone please post a simple copy and paste sort of thing to install the plugin.

i have the compiz installed theat came with gutsy and ccsm is also there.

---

### Post by jryprt on 2008-01-30
> **adz666 said:**
> i need help installing this. ive looked ato other threads but they dont seem to help.

can someone please post a simple copy and paste sort of thing to install the plugin.

i have the compiz installed theat came with gutsy and ccsm is also there.

Try [My Guide](http://ubuntuforums.org/showthread.php?t=659282)

---

### Post by adz666 on 2008-01-30
adam@adam-desktop:~$ wget -O /tmp/atlantis2.tar.gz 'http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=snapshot;h=fb6507c40216b13be567bd3d9501b5c598e084cd;sf=tgz'
--14:32:52--  [http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=snapshot;h=fb6507c40216b13be567bd3d9501b5c598e084cd;sf=tgz](http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=snapshot;h=fb6507c40216b13be567bd3d9501b5c598e084cd;sf=tgz)
           => `/tmp/atlantis2.tar.gz'
Resolving gitweb.compiz-fusion.org... 195.114.19.35
Connecting to gitweb.compiz-fusion.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [   <=>                               ] 186,322      322.47K/s             

14:32:53 (322.10 KB/s) - `/tmp/atlantis2.tar.gz' saved [186322]

adam@adam-desktop:~$ make
make: *** No targets specified and no makefile found. Stop.
adam@adam-desktop:~$ 
adam@adam-desktop:~$

---

### Post by jryprt on 2008-01-30
```
wget -O /tmp/atlantis2.tar.gz 'http://gitweb.compiz-fusion.org/?p=users/metastability/atlantis2;a=snapshot;h=fb6507c40216b13be567bd3d9501b5c598e084cd;sf=tgz'

```
```
tar -xf '/tmp/atlantis2.tar.gz' -C ~/compiz/
```
```
cd ~/compiz/atlantis2
```
```
make
```
```
sudo make install
```
Let me know if you get it.

---

### Post by ddaddy2420 on 2008-02-16
I too am having trouble getting past the first step.  i am getting this error:

I cut and pasted this in:
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

and i get this error eventually:
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb Hash Sum mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

The only disk i have is the one i created from the online file.  However, i thought i installed this on the computer so that i would no longer have to use this disk.

---

### Post by ddaddy2420 on 2008-02-16
bump

---

### Post by atryus28 on 2008-03-01
I was having a similar issue that I just resolved.  The CD hash was wrong.  removing the the CD from the repository list fixed the issue.  Try removing the bad repository and reentering it if needed.  Hope this helps.  I just resolved it myself about 5 minutes ago and found this post in my searching.

---

### Post by zelrikriando on 2008-05-14
I have the following error :

bcop'ing  : build/atlantis.xml -> build/atlantis_options.h/bin/sh: --header=build/atlantis_options.h: not found
make: *** [build/atlantis_options.h] Error 127

---

