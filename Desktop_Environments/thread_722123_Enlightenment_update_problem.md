---
title: "Enlightenment update problem"
date: 2008-03-12
forum: Desktop Environments
---

### Post by Nobby on 2008-03-12
Hi, I'm running OpenGEU and some enlightenment updates came up in the package manager today.  When I went to install them, I ran into some errors, and now I have some broken dependencies.
When I run apt-get install -f I get the following:
```

The following extra packages will be installed:
  libevas-engines
The following NEW packages will be installed:
  libevas-engines
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
29 not fully installed or removed.
Need to get 0B/48.7kB of archives.
After unpacking 201kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154492 files and directories currently installed.)
Unpacking libevas-engines (from .../libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/evas/modules/engines/buffer/linux-gnu-i486/module.so', which is also in package libevas0-engine-buffer
Errors were encountered while processing:
 /var/cache/apt/archives/libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Would it be safe to delete that module.so file that is mentioned?

---

### Post by scubajeff on 2008-03-12
I have the same problem. I believe somethings went wrong when they built the package.

---

### Post by Nobby on 2008-03-13
Anyone know how I might fix this problem?  I can't perform any updates while this is broken :(

---

### Post by Darkstone007 on 2008-03-13
You don't want to remove the file module.so, since it will prevent your Enligtenment from starting. If you have done it already, start a failsafe terminal and do the following:

cd /var/cache/apt/archives
mkdir tmp
dpkg-deb -x libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb tmp
cd tmp/usr/lib/evas/modules/engines/buffer/linux-gnu-i486
cp module.so /usr/lib/evas/modules/engines/buffer/linux-gnu-i486

This will bring your Enligtenment back to life, but will not fix the update issue. Someone smarter than me will (hopefully) fix that.

---

### Post by Nobby on 2008-03-13
Thanks for the tip Darkstone.  Luckily I haven't removed the module.so file yet so my enlightenment desktop still works.  Just can't perform any updates or install any new packages.....I've been trawling the internet for any answers but nothing has come up.  Does anyone know how I might fix this problem :confused:

---

### Post by Drone4four on 2008-03-13
I've got the same problem with the latest e17 packages for Gutsy.  This error is really annoying because I can't install **anything**.

---

### Post by Nobby on 2008-03-14
Well I seem to have found a work-around to this problem by following some of the steps mentioned in this site: [http://www.miketaylor.org.uk/tech/wxinmfpl/debian.html](http://www.miketaylor.org.uk/tech/wxinmfpl/debian.html)

First I did
```
sudo dpkg --force-depends -r libevas0-engine-buffer
```

Then
```
sudo dpkg -i /var/cache/apt/archives/libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb
```

And finally
```
sudo dpkg -i /var/cache/apt/archives/libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb
```

This installed the problem file but then it wouldn't install the package libevas0.  So I just repeated the above steps using the info in the new error message that apt threw up.

Everything seems to work ok, & I can update/install packages again :)  Fingers crossed I haven't busted something behind the scenes.

---

### Post by Darkstone007 on 2008-03-14
Thanks Nobby, I got it to run too. It took some package manipulation, but now I'm smarter for it :)

---

### Post by c0mp13371331337 on 2008-03-17
Thanks a ton, Nobby!  Your expertise has saved me many hours of frustration!  Oddly enough, I seem to remember a similar dependancy nightmare one of the past times a bunch of Enlightenment updates were released.  Although if I recall, it was a much simpler fix than it was this time around.  Kudos to you for taking the time to post the answer to an obviously widespread issue.

---

### Post by Drone4four on 2008-03-19
So I can install stuff again, which is great, but I can't install anything which requires EFL libraries.  Like I just tried to install eclair and this is what I got:

```
drone4four@ubuntu:~$ sudo apt-get install eclair
[sudo] password for drone4four:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  eclair: Depends: libemotion0 but it is not going to be installed
          Depends: libepsilon0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libtagc0 (>= 1.4) but it is not going to be installed
          Depends: libemotion0-xine but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
  enlightenment: Depends: enlightenment-data (= 1:0.16.999.042+cvs20080309-0gutsy2) but 1:0.16.999.042+cvs20080309-0gutsy1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So I try apt-get -f install:

```
drone4four@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libevas-loader-png libevas-loader-svg libevas-loader-tiff libevas-loader-xpm
  libevas-loaders-all libevas-loader-eet libevas-loader-gif
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  enlightenment-data
The following packages will be upgraded:
  enlightenment-data
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
3 not fully installed or removed.
Need to get 0B/6387kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... E: Sub-process /usr/bin/dpkg exited unexpectedly
drone4four@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libevas-loader-png libevas-loader-svg libevas-loader-tiff libevas-loader-xpm l
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  enlightenment-data
The following packages will be upgraded:
  enlightenment-data
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
3 not fully installed or removed.
Need to get 0B/6387kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154823 files and directories currently installed.)
Preparing to replace enlightenment-data 1:0.16.999.042+cvs20080309-0gutsy1 (usin
Ignoring nonregistered document enlightenment
Unpacking replacement enlightenment-data ...
Setting up ubuntu-docs (7.10.5) ...

Setting up enlightenment-data (1:0.16.999.042+cvs20080309-0gutsy2) ...

Setting up enlightenment (1:0.16.999.042+cvs20080309-0gutsy2) ...

Setting up e17 (1:0.16.999.042+cvs20080309-0gutsy2) ...
drone4four@ubuntu:~$ 
```

I hoped this would fix everything, but eclair still won't install.  Maybe I need to do a sudo apt-get install upgrade?

```
drone4four@ubuntu:~$ sudo apt-get upgrade e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libevas0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/236kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154823 files and directories currently installed.)
Preparing to replace libevas0 0.9.9.042+cvs20080207-0gutsy1 (using .../libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb) ...
Unpacking replacement libevas0 ...
Replacing files in old package libevas-loader-eet ...
Replacing files in old package libevas-loader-gif ...
dpkg: error processing /var/cache/apt/archives/libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/evas/modules/loaders/jpeg/linux-gnu-i486/module.so', which is also in package libevas0-loader-jpeg
Errors were encountered while processing:
 /var/cache/apt/archives/libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
drone4four@ubuntu:~$ 
```

Let's see if eclair will install now:

```
drone4four@ubuntu:~$ sudo apt-get install eclair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevas-loader-png libevas-loader-svg libevas-loader-tiff libevas-loader-xpm libevas-loaders-all libevas-loader-eet libevas-loader-gif
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libemotion0 libemotion0-xine libepeg0 libepsilon0 libesmart0 libtagc0
Suggested packages:
  epeg-bin
The following NEW packages will be installed:
  eclair libemotion0 libemotion0-xine libepeg0 libepsilon0 libesmart0 libtagc0
0 upgraded, 7 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 688kB of archives.
After unpacking 1606kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://e17.dunnewind.net gutsy/e17 libemotion0 0.1.0.042+cvs20080309-0gutsy1 [12.9kB]
Get:2 http://us.archive.ubuntu.com gutsy/main libtagc0 1.4-8 [9272B]
Get:3 http://e17.dunnewind.net gutsy/e17 libepeg0 0.9.1.042+cvs20080309-0gutsy2 [12.5kB]
Get:4 http://e17.dunnewind.net gutsy/e17 libepsilon0 0.3.0.012+cvs20080309-0gutsy2 [44.3kB]
Get:5 http://e17.dunnewind.net gutsy/e17 libesmart0 0.9.0.042+cvs20080309-0gutsy1 [36.4kB]
Get:6 http://e17.dunnewind.net gutsy/e17 libemotion0-xine 0.1.0.042+cvs20080309-0gutsy1 [15.0kB]
Get:7 http://e17.dunnewind.net gutsy/e17 eclair 0.0.1+cvs20080309-0gutsy1 [558kB]
Fetched 688kB in 1s (408kB/s)  
Selecting previously deselected package libemotion0.
(Reading database ... 154823 files and directories currently installed.)
Unpacking libemotion0 (from .../libemotion0_0.1.0.042+cvs20080309-0gutsy1_i386.deb) ...
Selecting previously deselected package libepeg0.
Unpacking libepeg0 (from .../libepeg0_0.9.1.042+cvs20080309-0gutsy2_i386.deb) ...
Selecting previously deselected package libepsilon0.
Unpacking libepsilon0 (from .../libepsilon0_0.3.0.012+cvs20080309-0gutsy2_i386.deb) ...
Selecting previously deselected package libesmart0.
Unpacking libesmart0 (from .../libesmart0_0.9.0.042+cvs20080309-0gutsy1_i386.deb) ...
Selecting previously deselected package libtagc0.
Unpacking libtagc0 (from .../libtagc0_1.4-8_i386.deb) ...
Selecting previously deselected package libemotion0-xine.
Unpacking libemotion0-xine (from .../libemotion0-xine_0.1.0.042+cvs20080309-0gutsy1_i386.deb) ...
Selecting previously deselected package eclair.
Unpacking eclair (from .../eclair_0.0.1+cvs20080309-0gutsy1_i386.deb) ...
Setting up libkrb53 (1.6.dfsg.1-7ubuntu0.1) ...

Setting up libkadm55 (1.6.dfsg.1-7ubuntu0.1) ...

Setting up libkrb5-dev (1.6.dfsg.1-7ubuntu0.1) ...
Setting up libemotion0 (0.1.0.042+cvs20080309-0gutsy1) ...

Setting up libepeg0 (0.9.1.042+cvs20080309-0gutsy2) ...

Setting up libepsilon0 (0.3.0.012+cvs20080309-0gutsy2) ...

Setting up libesmart0 (0.9.0.042+cvs20080309-0gutsy1) ...

Setting up libtagc0 (1.4-8) ...

Setting up libemotion0-xine (0.1.0.042+cvs20080309-0gutsy1) ...
Setting up eclair (0.0.1+cvs20080309-0gutsy1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
drone4four@ubuntu:~$ 
```


Wow, it worked! 

w00t

---

### Post by Drone4four on 2008-04-04
Now e17 won't even load.  libevas won't upgrade.  Here is my upgrade command:

```
drone4four@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libevas0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/236kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154830 files and directories currently installed.)
Preparing to replace libevas0 0.9.9.042+cvs20080207-0gutsy1 (using .../libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb) ...
Unpacking replacement libevas0 ...
dpkg: error processing /var/cache/apt/archives/libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/evas/modules/loaders/jpeg/linux-gnu-i486/module.so', which is also in package libevas0-loader-jpeg
Errors were encountered while processing:
 /var/cache/apt/archives/libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
drone4four@ubuntu:~$ 
```

Does e17 not load anymore for you folks?

---

### Post by Genesius on 2008-04-09
Tru "Sudo dpkg -i --force-overwrite /var/cache/apt/archives/libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb"

If that doesn't work, cd to /var/cache/apt/archives and just "sudo dpkg -i --force-overwrite libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb"

---

### Post by smartboyathome on 2008-04-10
> **Genesius said:**
> Tru "Sudo dpkg -i --force-overwrite /var/cache/apt/archives/libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb"

If that doesn't work, cd to /var/cache/apt/archives and just "sudo dpkg -i --force-overwrite libevas0_0.9.9.042+cvs20080309-0gutsy2_i386.deb"

Those two commands do the same thing, so there is no point trying the second if the fist command doesn't work.

---

### Post by Genesius on 2008-04-10
That's the way it should be, but for some reason the first doesn't work on my system but the second one does. YMMV, of course. . .

---

### Post by Drone4four on 2008-04-11
The first doesn't work.  The second one worked like a charm. =D

---

### Post by Genesius on 2008-04-12
W00t! So it's not just me, then!

---

