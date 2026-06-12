---
title: "[SOLVED] source repository in sources.list"
date: 2008-03-27
forum: Debian
---

### Post by keratos on 2008-03-27
Why can I not see any linux source packages in the repos:

sources.list:
```

deb http://debian.virginmedia.com/ testing main contrib non-free      
deb-src http://debian.virginmedia.com/ testing main contrib non-free  

deb http://debian.virginmedia.com/ etch main contrib non-free    
deb-src http://debian.virginmedia.com/ etch main contrib non-free     

deb http://security.debian.org/ etch/updates main 
deb-src http://security.debian.org/ etch/updates main  

#deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

```

then
```

apt-get update -qV
Hit http://security.debian.org etch/updates Release.gpg
Ign http://security.debian.org etch/updates/main Translation-en_GB
Hit http://security.debian.org etch/updates Release
Ign http://security.debian.org etch/updates/main Packages/DiffIndex
Hit http://debian.virginmedia.com testing Release.gpg
Ign http://debian.virginmedia.com testing/main Translation-en_GB
Ign http://debian.virginmedia.com testing/contrib Translation-en_GB
Ign http://debian.virginmedia.com testing/non-free Translation-en_GB
Hit http://debian.virginmedia.com etch Release.gpg
Ign http://debian.virginmedia.com etch/main Translation-en_GB
Ign http://debian.virginmedia.com etch/contrib Translation-en_GB
Ign http://security.debian.org etch/updates/main Sources/DiffIndex
Hit http://security.debian.org etch/updates/main Packages
Ign http://debian.virginmedia.com etch/non-free Translation-en_GB
Hit http://security.debian.org etch/updates/main Sources
Hit http://debian.virginmedia.com testing Release
Hit http://debian.virginmedia.com etch Release
Hit http://debian.virginmedia.com testing/main Packages/DiffIndex
Hit http://debian.virginmedia.com testing/contrib Packages/DiffIndex
Hit http://debian.virginmedia.com testing/non-free Packages/DiffIndex
Hit http://debian.virginmedia.com testing/main Sources/DiffIndex
Hit http://debian.virginmedia.com testing/contrib Sources/DiffIndex
Hit http://debian.virginmedia.com testing/non-free Sources/DiffIndex
Ign http://debian.virginmedia.com etch/main Packages/DiffIndex
Ign http://debian.virginmedia.com etch/contrib Packages/DiffIndex
Ign http://debian.virginmedia.com etch/non-free Packages/DiffIndex
Ign http://debian.virginmedia.com etch/main Sources/DiffIndex
Ign http://debian.virginmedia.com etch/contrib Sources/DiffIndex
Ign http://debian.virginmedia.com etch/non-free Sources/DiffIndex
Hit http://debian.virginmedia.com etch/main Packages
Hit http://debian.virginmedia.com etch/contrib Packages
Hit http://debian.virginmedia.com etch/non-free Packages
Hit http://debian.virginmedia.com etch/main Sources
Hit http://debian.virginmedia.com etch/contrib Sources
Hit http://debian.virginmedia.com etch/non-free Sources
Reading package lists...

# apt-cache search linux.*2.6.22-3.*
linux-headers-2.6.22-3 - Common header files for Linux 2.6.22
linux-headers-2.6.22-3-486 - Header files for Linux 2.6.22 on x86
linux-headers-2.6.22-3-686 - Header files for Linux 2.6.22 on PPro/Celeron/PII/PIII/P4
linux-headers-2.6.22-3-686-bigmem - Header files for Linux 2.6.22 on PPro/Celeron/PII/PIII/P4
linux-headers-2.6.22-3-all - All header files for Linux 2.6.22
linux-headers-2.6.22-3-all-i386 - All header files for Linux 2.6.22
linux-headers-2.6.22-3-amd64 - Header files for Linux 2.6.22 on AMD64
linux-headers-2.6.22-3-k7 - Header files for Linux 2.6.22 on AMD K7
linux-headers-2.6.22-3-vserver - Common header files for Linux 2.6.22
linux-headers-2.6.22-3-vserver-686 - Header files for Linux 2.6.22 on PPro/Celeron/PII/PIII/P4
linux-headers-2.6.22-3-vserver-k7 - Header files for Linux 2.6.22 on AMD K7
linux-image-2.6-486 - Linux 2.6 image on x86
linux-image-2.6-686 - Linux 2.6 image on PPro/Celeron/PII/PIII/P4
linux-image-2.6-686-bigmem - Linux 2.6 image on PPro/Celeron/PII/PIII/P4
linux-image-2.6-amd64 - Linux 2.6 image on AMD64
linux-image-2.6-k7 - Linux 2.6 image on AMD K7
linux-image-2.6-vserver-686 - Linux 2.6 image on PPro/Celeron/PII/PIII/P4
linux-image-2.6-vserver-k7 - Linux 2.6 image on AMD K7
linux-image-2.6.22-3-486 - Linux 2.6.22 image on x86
linux-image-2.6.22-3-686 - Linux 2.6.22 image on PPro/Celeron/PII/PIII/P4
linux-image-2.6.22-3-686-bigmem - Linux 2.6.22 image on PPro/Celeron/PII/PIII/P4
linux-image-2.6.22-3-amd64 - Linux 2.6.22 image on AMD64
linux-image-2.6.22-3-k7 - Linux 2.6.22 image on AMD K7
linux-image-2.6.22-3-vserver-686 - Linux 2.6.22 image on PPro/Celeron/PII/PIII/P4
linux-image-2.6.22-3-vserver-k7 - Linux 2.6.22 image on AMD K7
linux-support-2.6.22-3 - Support files for Linux 2.6.22
linux-tree-2.6.22 - Linux kernel source tree for building Debian kernel images

```

No source, only images and headers!

What gives good folk, where are the sources please ??????

p.s. I've installed linux-image-2.6.22-3-k7 - Linux 2.6.22 image on AMD K7.

```

uname -a
Linux desktop 2.6.22-3-k7 #1 SMP Mon Nov 12 09:12:50 UTC 2007 i686 GNU/Linux

```

---

### Post by keratos on 2008-03-27
SOLVED.

the mirror is crap.

any others are okay!!

---

### Post by Caraibes on 2008-03-27
Just for the record, I am pretty satisfied with my sources.list:
```
####################
## Debian Testing ##
####################

# Testing
deb http://ftp.br.debian.org/debian/ testing main non-free contrib
deb-src http://ftp.br.debian.org/debian/ testing main non-free contrib

#Testing Security updates
deb http://security.debian.org/ testing/updates main contrib
deb-src http://security.debian.org/ testing/updates main contrib

#debian multimedia repository (http://lxer.com/module/forums/t/24283/)
deb ftp://linorg.usp.br/debian-marillat/ testing main
deb-src ftp://linorg.usp.br/debian-marillat/ testing main

# Official site for latest version of skype.
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Google picasa 
#(wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - )
# or (gpg --keyserver subkeys.pgp.net --recv A040830F7FAC5991 && gpg --export --armor A040830F7FAC5991 | sudo apt-key add - )
deb http://dl.google.com/linux/deb/ stable non-free

### Opera Browser (http://deb.opera.com/) ###
deb http://deb.opera.com/opera/ testing non-free

```

---

### Post by keratos on 2008-03-27
have you used the netselect app to find your speediest mirror !! ?

apt-get install netselect

---

### Post by Caraibes on 2008-03-28
> **keratos said:**
> have you used the netselect app to find your speediest mirror !! ?

apt-get install netselect

Thank you, for that good idea !

I just did it, and it came up with a result, so I updated that part of my sources.list:
```
# Testing
deb ftp://bigmirror.crossbowproject.net/pub/debian/ testing main non-free contrib
deb-src ftp://bigmirror.crossbowproject.net/pub/debian/ testing main non-free contrib
```

---

### Post by keratos on 2008-03-28
> **Caraibes said:**
> Thank you, for that good idea !

I just did it, and it came up with a result, so I updated that part of my sources.list:
```
# Testing
deb ftp://bigmirror.crossbowproject.net/pub/debian/ testing main non-free contrib
deb-src ftp://bigmirror.crossbowproject.net/pub/debian/ testing main non-free contrib
```

without seeing your results I dont know if these is "the best" for you. 

Anyway, the score to the right of the mirror tests is the one to look for, lower is better! (less hops , lower ms time).

Hope that helps.

---

### Post by Caraibes on 2008-03-31
> **keratos said:**
> without seeing your results I dont know if these is "the best" for you. 

Here's an example of 2 servers I had as "fastest":
```
spc1:/home/martin# netselect -vv ftp://debian.crosslink.net/debian/
Running netselect to choose 1 out of 1 address.         
...........
ftp://debian.crosslink.net/debian/     120 ms  18 hops   90% ok ( 9/10) [  372]
  372 ftp://debian.crosslink.net/debian/
spc1:/home/martin# netselect -vv ftp://bigmirror.crossbowproject.net/pub/debian/
Running netselect to choose 1 out of 1 address.         
............
ftp://bigmirror.crossbowproject.net/pub/debian/    109 ms  18 hops  100% ok (10/10) [  305]
  305 ftp://bigmirror.crossbowproject.net/pub/debian/

```

---

