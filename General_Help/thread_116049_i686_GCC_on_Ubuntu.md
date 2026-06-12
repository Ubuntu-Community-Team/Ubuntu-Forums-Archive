---
title: "i686 GCC on Ubuntu?"
date: 2006-01-11
forum: General Help
---

### Post by robstoffers on 2006-01-11
Hi,

What is the easiest way to get a i686 compiler installed on my Ubuntu Breezy system? I can only find i386 packages in the archives, I need i686 so I can distcc with a gentoo laptop. I'm trying to compile KDE on my laptop, using distcc with a Ubuntu Breezy PC. Followed
the directions at [http://ubuntuforums.org/archive/index.php/t-83186.html]("http://ubuntuforums.org/archive/index.php/t-83186.html") and
[http://www.gentoo.org/doc/en/distcc.xml]("http://www.gentoo.org/doc/en/distcc.xml"). GCC versions are 3.3.6 on both PCs (although 4 is also 
installed on the ubuntu PC. Build-essential is installed.

Below is the error on the Gentoo laptop when distcc:

distccd[23274] (dcc_execvp) ERROR: failed to exec i686-pc-linux-gnu-g++: No such file or directory
distcc[20101] ERROR: compile exceptions.cpp on 192.168.0.2 failed with exit code 110

---

### Post by xxMEL0Nxx on 2006-04-10
[QUOTE=robstoffers]Hi,

What is the easiest way to get a i686 compiler installed on my Ubuntu Breezy system? I can only find i386 packages in the archives, I need i686 so I can distcc with a gentoo laptop. I'm trying to compile KDE on my laptop, using distcc with a Ubuntu Breezy PC. Followed
the directions at [http://ubuntuforums.org/archive/index.php/t-83186.html]("http://ubuntuforums.org/archive/index.php/t-83186.html") and
[http://www.gentoo.org/doc/en/distcc.xml]("http://www.gentoo.org/doc/en/distcc.xml"). GCC versions are 3.3.6 on both PCs (although 4 is also 
installed on the ubuntu PC. Build-essential is installed.

Below is the error on the Gentoo laptop when distcc:

distccd[23274] (dcc_execvp) ERROR: failed to exec i686-pc-linux-gnu-g++: No such file or directory
distcc[20101] ERROR: compile exceptions.cpp on 192.168.0.2 failed with exit code 110[/QUOTE]


I had the same problem, I'd make a symlink gcc --> gcc-3.4 in ubuntu, and added 


```

CC='gcc' 
CXX='c++'

```

to /etc/make.conf in gentoo

---

### Post by nazish on 2006-04-10
i think  ** melon** is right

---

