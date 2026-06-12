---
title: "unable to execute existing binary file : No such file or directory"
date: 2009-04-28
forum: General Help
---

### Post by DonBusi on 2009-04-28
Hi guys,

I've got a rather strange problem with w_scan (a utility to scan for channels on a DVB-C or -T card) that I downloaded from [http://wirbel.htpc-forum.de/w_scan/index2.html](http://wirbel.htpc-forum.de/w_scan/index2.html)

When I try to execute the program, bash tells me that the file does not exist.

```

xbox@HypnoToad:/usr/src/w_scan$ sudo ls -la ./w*
-rwxr-xr-x 1 root root 104191 2008-11-06 21:44 ./w_scan
-rwxr-xr-x 1 root root  22628 2009-04-27 23:10 ./w_scan_start.sh
xbox@HypnoToad:/usr/src/w_scan$ sudo ./w_scan
sudo: unable to execute ./w_scan: No such file or directory

```My Box runns a Ubuntu 8.10 with all the latest patches, kernel-sources and -headers are also installed.
```

xbox@HypnoToad:/usr/src/w_scan$ uname -a
 Linux HypnoToad 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux
 
```Can anyone tell me what's wrong? What do I have to change to get this file executed?

Thanx for you help,
Don

---

### Post by zvacet on 2009-04-28
Did you run **make** command as is described on  w_scan web page?Try run 

```
sudo ./w_scan_start.sh
```

---

### Post by DonBusi on 2009-04-29
Hi zvacet,

as **make** fails with an error (see below). I tried to just use the pre-compiled binary that is also included in the tarball. => w_scan-20081106/w_scan

...which shows the strange behaviour mentioned in my original post.

If I try to run the script that is also included in the tarball, I get also an error:

```

root@HypnoToad:/usr/src/w_scan-20081106# ./w_scan_start.sh
./w_scan_start.sh: 202: Syntax error: "(" unexpected
```I'm absolutely clueless... the same binary on an other Ubuntu (8.04) box executes fine.

Thanx for any help!
Don,

Here's the error that **make **produces:
```

root@HypnoToad:/usr/src/w_scan-20081106# make
gcc -MD -g -Wall -O2 --static -c dump-vdr.c -o dump-vdr.o
dump-vdr.c:26:19: error: stdio.h: No such file or directory
In file included from dump-vdr.c:27:
dump-vdr.h:29:20: error: stdint.h: No such file or directory
In file included from dump-vdr.c:27:
dump-vdr.h:95: error: expected ")" before "*" token
dump-vdr.h:100: error: expected ")" before "*" token
dump-vdr.c:95: error: expected ")" before "*" token
dump-vdr.c:124: error: expected ")" before "*" token
make: *** [dump-vdr.o] Error 1
```

---

### Post by Brandon Williams on 2009-04-29
Did you install build-essential on the box that you're trying to run make on now? If the system can't find a standard header like stdio.h, you most likely don't have build-essential installed.

Also, run file on the pre-compiled binary. If it says anything other than 'ELF 32-bit LSB executable', then you won't be able to run it on an i386 machine without adding some non-standard binary support to your system.

---

### Post by DonBusi on 2009-04-30
Hi,

Thanx for you help.

**build-essential** is not installed...and for some strange reason apt refuses to install it. ...some conflict with libc6 & libc6-dev that cannot be resolved. I'll try to resolve this later...or do you think it is also necessary for the execution of the binary file?

**file w_scan **says 
```

xbox@HypnoToad:/usr/src/w_scan$ file w_scan
w_scan: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), not stripped

```

So I still have no idea why I cannot execute the binary file.

Cheers,
Don

---

### Post by Brandon Williams on 2009-04-30
Try running the command without sudo to see what kind of error message you get. Also, try specifying the full path to the executable, as in: sudo /usr/src/w_scan/w_scan

This is just to make sure that there isn't some strange issue related to sudo.

---

### Post by taurus on 2009-04-30
The problem is that w_scan is a 32bit app but you are running 64bit.  Until you install a library for 32bit, ia32-libs, on your machine first, you won't be able to run those 32bit apps.

---

### Post by DonBusi on 2009-05-04
Hi taurus,
   
   thanx for the tip. I tried to install the suggested library. It turns out that it depends on a library that depends on .... well that's where I my system stumbles over the conflict with libc6 & libc6-dev that I mentioned earlier.  
   
   So I guess the mystery why I cannot execute w_scan is solved and I now have to fix my problem with the libc6. => As Ubuntu 9.04 is out now, I'll just do a fresh install.  
   
   Thanx to everybody for your help! 
   Don

---

### Post by dcstar on 2009-05-04
> **taurus said:**
> The problem is that w_scan is a 32bit app but you are running 64bit.  Until you install a library for 32bit, ia32-libs, on your machine first, you won't be able to run those 32bit apps.

That does not necessarily allow 32-bit binaries to run, AFAIK you need to set up a 32-bit chroot environment, like these (but with modifications for the version you are using):

[http://wiki.ndgf.org/display/ndgfwiki/Procedure+for+IA32+chroot](http://wiki.ndgf.org/display/ndgfwiki/Procedure+for+IA32+chroot)
[http://swiki.hfbk-hamburg.de:8888/MusicTechnology/879](http://swiki.hfbk-hamburg.de:8888/MusicTechnology/879)

---

### Post by DonBusi on 2009-05-11
Hi all, 

on my newly installed Jaunty w_scan works perfectly fine. So in a way my problem is solved ... even tough I don't realy know the reason why it didn't work in the first place. 

For anyone having problems with the w_scan binary from the project web-site... try installing it via the apt-get from the ubuntu repositories ([w-scan]("http://packages.ubuntu.com/jaunty/w-scan")). 

Thanx for all your help & inputs,
Don.

---

### Post by DonBusi on 2009-05-11
ups sorry, doublepost.

---

