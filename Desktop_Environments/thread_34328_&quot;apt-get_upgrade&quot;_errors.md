---
title: "&quot;apt-get upgrade&quot; errors"
date: 2005-05-14
forum: Desktop Environments
---

### Post by Cal Paterson on 2005-05-14
I just switched to linux, and I'm trying to download updates/upgrades for my install using apt-get, but I'm getting some problems once the files have been downloaded.  

After using the "apt-get upgrade" command, I get:

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb (--unpack):
 malloc failed (2014345335 bytes): Cannot allocate memory
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

I'm a real linux/unix newbie, so please keep replies simplistic.  Thankyou.

---

### Post by Xian on 2005-05-14
Try removing that file in error and attempt the update again.
Open a terminal and type this line:

```
sudo rm -f /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb
```

---

### Post by Cal Paterson on 2005-05-14
Thanks for the fast reply.

I don't really understand this, but entering that command doesn't actually do anything on this end - BASH just asks for my password and then does nothing and moves to the next line.  

```
$ sudo rm -f /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb
Password:

```

Perhaps I have something configured wrong?  

I tried runnning the Software Updates facility, but I got another, similar error with the next progam on the list to download:

```
E: /var/cache/apt/archives/libgnutls11_1.0.16-13ubuntu0.1_i386.deb:  malloc failed (2014345335 bytes): Cannot allocate memory
```

---

### Post by Xian on 2005-05-14
Try entering this into a terminal:

```
sudo apt-get install --reinstall gzip
```

How much memory does your system have?
Shut down any unneeded programs during this session.

---

### Post by Xian on 2005-05-14
BTW, if this doesn't work then the next couple of things you will want to check is whether or not your swap file is being correctly mounted, and to verify that the partition /var is mounted on is not corrupt. This can be done using the [fsck](http://publibn.boulder.ibm.com/doc_link/en_US/a_doc_lib/cmds/aixcmds2/fsck.htm) command.

---

### Post by Cal Paterson on 2005-05-15
Ok, I ran that command, and got the following:

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb (--unpack):
 malloc failed (2014345335 bytes): Cannot allocate memory
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb
Processing was halted because there were too many errors.
W: Couldn't stat source package list http://download.videolan.org sid/main Packages (/var/lib/apt/lists/download.videolan.org_pub_videolan_debian_dists_sid_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list securihttpty..com hoary-security/universe Packages (/var/lib/apt/lists/securihttpty..com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

This box isn't exactly immense; 1ghz x86 cpu/256 RAM.

The System Monitor Utility is showing that the swap is in use, so I think it might be my HD,  I'm gonna have to go search around for details on the fsck command, but is it safe to use it on the same partition I'm booted off (I only have 1 HD)?

---

