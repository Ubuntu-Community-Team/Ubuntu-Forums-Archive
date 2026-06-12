---
title: "Garry's Mod"
date: 2016-12-21
forum: Gaming &amp; Leisure
---

### Post by oblivion12 on 2016-12-21
I am getting this problem when I attempt to open up Garry's Mod.

Couldn't load: /home/oblivion12/.local/share/Steam/steamapps/common/GarrysMod/garrysmod/bin/client.so
Reason: Libgpg-error.so.0: cannot open shared object file: No such file or directiry

Please try again.

```
 sudo apt-get ia32-libs 
``` isn't a package (I've already tried this.)

---

### Post by oldrocker99 on 2016-12-22
The ia-32libs metapackage no longer exists, and more's the pity. Try this:```
sudo apt-get install libgpg-error0:i386
```

---

### Post by oblivion12 on 2016-12-22
When I attempt to download stuff I keep getting this.

```
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
oblivion12@AnonHFUser:~$ 

```
When I attempt 

```
 apt-get -f install 
```

I get this: 
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
oblivion12@AnonHFUser:~$
```

---

### Post by oldrocker99 on 2016-12-23
You **have** to use *sudo* before **any** operation like installing programs. That's why you got that "are you root?" message.

---

### Post by oblivion12 on 2016-12-23
```
oblivion12@AnonHFUser:~$ sudo apt-get -f install
[sudo] password for oblivion12: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libstdc++-5-dev
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 179 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,262 kB of archives.
After this operation, 6,936 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 262044 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu5) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu5_amd64.deb (--unpack):
 trying to overwrite '/usr/include/fpu_control.h', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu5
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


oblivion12@AnonHFUser:~$  sudo apt-get install libgpg-error0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgpgp-error0:i386
oblivion12@AnonHFUser:~$ 

 
```

---

### Post by oldrocker99 on 2016-12-23
That's lib**gpg**-error0:i386, not "libgpgp-error0:i386." Program names must have exact spelling. The -dev 64-bit package isn't necessary on your system, it's for compiling programs.

---

### Post by oblivion12 on 2016-12-23
Ok I fixed it, but I get this:
```

trying to overwrite '/usr/include/fpu_control.h', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu5
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
oblivion12@AnonHFUser:~$ 
```


Everything I do leads to the **-dev-i386**

---

### Post by oblivion12 on 2016-12-23
Everything was solved by this thread: [https://ubuntuforums.org/showthread.php?t=2323994&page=5](https://ubuntuforums.org/showthread.php?t=2323994&page=5)

Then to fix the Garry's Mod problem

```
 
sudo apt-get install libgpg-error0:i386 
```

---

### Post by oldrocker99 on 2016-12-24
Great! Please mark your thread as [SOLVED].

---

