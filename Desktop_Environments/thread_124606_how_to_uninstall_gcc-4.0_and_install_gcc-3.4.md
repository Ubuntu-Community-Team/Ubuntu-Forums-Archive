---
title: "how to uninstall gcc-4.0 and install gcc-3.4?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Cynosure on 2006-02-01
Hi,

I'm new to ubuntu.
I used apt-get install build-essential and it installed gcc 4.0.
I want to uninstall it and install gcc 3.4

Can anyone please help?

Thanks in advance

---

### Post by Sutekh on 2006-02-01
gcc-3.4 is in the repositories

```

sudo apt-get install gcc-3.4
```
then to use 3.4 rather than 4.0
```

CC=gcc-3.4
export CC
```
then off you go.
If you want to use 3.4 permanently
```

sudo apt-get remove gcc-4.0
```
will get rid of 4.0

---

### Post by Cynosure on 2006-02-01
Hi thanks for the reply.

I am getting this message:

sudo apt-get install gcc-3.4:KS 
Reading package lists... Done
Building dependency tree... Done
Package gcc-3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gcc-3.4 has no installation candidate

---

### Post by Sutekh on 2006-02-01
[QUOTE=Cynosure]Hi thanks for the reply.

I am getting this message:

sudo apt-get install gcc-3.4:KS 
Reading package lists... Done
Building dependency tree... Done
Package gcc-3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gcc-3.4 has no installation candidate[/QUOTE]
Ok thats not very nice is it?

Perhaps you could try using Synaptic and make sure I was right about it being in the repositories, or use the command to search for it using apt-get
```

sudo apt-cache search gcc
```
and see what gcc options you get.  Hopefully gcc 3.4 will come up.


Otherwise I found a great HOWTO, that people use to install 3.4 offline.  You could adapt it easily to install gcc-3.4 manually.  
[Ubuntu Forums - HOWTO: Install gcc-3.4 via apt-get without internet connection - by ]("http://ubuntuforums.org/showthread.php?t=79896")[blastus]("http://ubuntuforums.org/member.php?u=33611")

---

### Post by Cynosure on 2006-02-02
Hi,

I read that link and did exactly what was written there.
But after the whole process i checked the gcc version by gcc --version and it is still 4.0

Do I need to do anything else?

Thanks

---

### Post by Sutekh on 2006-02-02
Ok, so were you able to install gcc-3.4 by downloading the .deb files linked in the Howto?  (If you were able to install gcc-3.4 without error, ignore the next bit)

Instead of going through the whole motion of setting up a local repository, you can install the .deb files manually using the following commands.  Go to the folder where you downloaded the .debs to, and
```
sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i gcc-3.4_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb

```
and then
```

sudo apt-get install binutils
```


If this is (was) successful, you will have gcc-3.4 installed.  To use it you will need to use the command
```

export CC=gcc-3.4
```
This sets the C compiler to gcc-3.4.

---

