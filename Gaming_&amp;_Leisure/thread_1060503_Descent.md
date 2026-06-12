---
title: "Descent"
date: 2009-02-04
forum: Gaming &amp; Leisure
---

### Post by bobmatino17 on 2009-02-04
I have been playing Descent 3 for a while and i want to install Descent 1 & 2, would anybody know how to do that?

P.S.
I will play anyone in a TCP/IP match in D3.

---

### Post by jpeddicord on 2009-02-04
Moved to Gaming & Leisure. Community Cafe Games is pretty much just forum-based post games. :p

---

### Post by grossaffe on 2009-02-04
probably DOSbox

---

### Post by yabbadabbadont on 2009-02-04
[http://www.dxx-rebirth.com/](http://www.dxx-rebirth.com/)

---

### Post by bobmatino17 on 2009-02-05
thnx very much.

---

### Post by bobmatino17 on 2009-02-05
I'm 13 do i don't have that much experience in Linux. still the only kid on the Light Side in my school. How do you install them?

---

### Post by bobmatino17 on 2009-02-05
well.. i read the install.txt file which i should have done and tried to use scons to compile it and got...
```
tuxiscool@tuxiscool-desktop:~$ cd /home/tuxiscool/Desktop/d1x-rebirth_v0.55.1-src
tuxiscool@tuxiscool-desktop:~/Desktop/d1x-rebirth_v0.55.1-src$ sudo scons
scons: Reading SConscript files ...

===== D1X-Rebirth v0.55.1 (svn exported) =====

compiling on *NIX
building with OpenGL


scons: done reading SConscript files.
scons: Building targets ...
Compiling 2d/2dsline.c ...
In file included from include/gr.h:22,
                 from 2d/2dsline.c:63:
include/cfile.h:27:20: error: physfs.h: No such file or directory
In file included from include/cfile.h:35,
                 from include/gr.h:22,
                 from 2d/2dsline.c:63:
include/physfsx.h: In function &#8216;PHYSFSX_init&#8217;:
include/physfsx.h:56: warning: implicit declaration of function &#8216;PHYSFS_init&#8217;
include/physfsx.h:57: warning: implicit declaration of function &#8216;PHYSFS_permitSymbolicLinks&#8217;
include/physfsx.h:78: warning: implicit declaration of function &#8216;PHYSFS_getUserDir&#8217;
include/physfsx.h:78: warning: initialization makes pointer from integer without a cast
include/physfsx.h:82: warning: implicit declaration of function &#8216;PHYSFS_getDirSeparator&#8217;
include/physfsx.h:82: error: invalid type argument of &#8216;unary *&#8217;
include/physfsx.h:89: warning: implicit declaration of function &#8216;PHYSFS_setWriteDir&#8217;
include/physfsx.h:90: warning: implicit declaration of function &#8216;PHYSFS_getWriteDir&#8217;
include/physfsx.h:97: error: invalid type argument of &#8216;unary *&#8217;
include/physfsx.h:102: error: invalid type argument of &#8216;unary *&#8217;
include/physfsx.h:111: error: invalid type argument of &#8216;unary *&#8217;
include/physfsx.h:111: error: invalid type argument of &#8216;unary *&#8217;
include/physfsx.h:111: error: invalid type argument of &#8216;unary *&#8217;
include/physfsx.h:111: error: invalid type argument of &#8216;unary *&#8217;
include/physfsx.h:113: warning: implicit declaration of function &#8216;PHYSFS_mkdir&#8217;
include/physfsx.h:117: warning: implicit declaration of function &#8216;PHYSFS_addToSearchPath&#8217;
include/physfsx.h:120: warning: implicit declaration of function &#8216;PHYSFS_getBaseDir&#8217;
include/physfsx.h:122: warning: implicit declaration of function &#8216;PHYSFS_removeFromSearchPath&#8217;
include/physfsx.h:128: warning: implicit declaration of function &#8216;PHYSFS_getLastError&#8217;
include/physfsx.h:128: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;
include/physfsx.h: At top level:
include/physfsx.h:142: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:156: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:170: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:175: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:180: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:185: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:195: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:209: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:219: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h:229: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/physfsx.h: In function &#8216;PHYSFSX_getRealPath&#8217;:
include/physfsx.h:241: warning: implicit declaration of function &#8216;PHYSFS_getRealDir&#8217;
include/physfsx.h:241: warning: initialization makes pointer from integer without a cast
include/physfsx.h:242: warning: initialization makes pointer from integer without a cast
include/physfsx.h:247: warning: assignment makes pointer from integer without a cast
include/physfsx.h: In function &#8216;PHYSFSX_findFiles&#8217;:
include/physfsx.h:296: warning: implicit declaration of function &#8216;PHYSFS_enumerateFiles&#8217;
include/physfsx.h:296: warning: initialization makes pointer from integer without a cast
include/physfsx.h: At top level:
include/physfsx.h:323: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;PHYSFSX_getFreeDiskSpace&#8217;
include/physfsx.h:338: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
include/physfsx.h:363: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
include/physfsx.h:380: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
In file included from include/gr.h:22,
                 from 2d/2dsline.c:63:
include/cfile.h: In function &#8216;cfile_size&#8217;:
include/cfile.h:103: error: &#8216;PHYSFS_file&#8217; undeclared (first use in this function)
include/cfile.h:103: error: (Each undeclared identifier is reported only once
include/cfile.h:103: error: for each function it appears in.)
include/cfile.h:103: error: &#8216;fp&#8217; undeclared (first use in this function)
include/cfile.h:106: warning: implicit declaration of function &#8216;PHYSFS_openRead&#8217;
include/cfile.h:118: warning: implicit declaration of function &#8216;PHYSFS_fileLength&#8217;
include/cfile.h:119: warning: implicit declaration of function &#8216;PHYSFS_close&#8217;
include/cfile.h: At top level:
include/cfile.h:124: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/cfile.h:134: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/cfile.h:156: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PHYSFS_file&#8217;
include/cfile.h: In function &#8216;cfgets&#8217;:
include/cfile.h:165: warning: implicit declaration of function &#8216;cfgetc&#8217;
include/cfile.h:165: error: &#8216;fp&#8217; undeclared (first use in this function)
include/cfile.h:180: warning: implicit declaration of function &#8216;cfseek&#8217;
include/cfile.h: At top level:
include/cfile.h:203: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/cfile.h:216: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/cfile.h:229: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/cfile.h:242: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/cfile.h:255: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/cfile.h:268: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PHYSFS_file&#8217;
include/cfile.h: In function &#8216;cfile_read_vector&#8217;:
include/cfile.h:270: warning: implicit declaration of function &#8216;cfile_read_fix&#8217;
include/cfile.h:270: error: &#8216;file&#8217; undeclared (first use in this function)
include/cfile.h: At top level:
include/cfile.h:275: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PHYSFS_file&#8217;
include/cfile.h: In function &#8216;cfile_read_angvec&#8217;:
include/cfile.h:277: warning: implicit declaration of function &#8216;cfile_read_fixang&#8217;
include/cfile.h:277: error: &#8216;file&#8217; undeclared (first use in this function)
include/cfile.h: At top level:
include/cfile.h:282: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PHYSFS_file&#8217;
include/cfile.h: In function &#8216;cfile_read_matrix&#8217;:
include/cfile.h:284: error: &#8216;file&#8217; undeclared (first use in this function)
include/cfile.h:284: error: too many arguments to function &#8216;cfile_read_vector&#8217;
include/cfile.h:285: error: too many arguments to function &#8216;cfile_read_vector&#8217;
include/cfile.h:286: error: too many arguments to function &#8216;cfile_read_vector&#8217;
scons: *** [2d/2dsline.o] Error 1
scons: building terminated because of errors.
tuxiscool@tuxiscool-desktop:~/Desktop/d1x-rebirth_v0.55.1-src$ 


```

same thing with gcc

---

### Post by donkyhotay on 2009-02-05
ALthough DOSbox works I would recommend using D2X instead. I used to use it for windows (due to DOS issues with XP) and it worked great. Not certain how well it works with linux but I do know they have a linux port so I assume it's the same. Hmm... maybe I should see about installing descent again...


//edit: Oops, someone beat me to my suggestion (c:

---

### Post by Brebs on 2009-02-05
> **bobmatino17 said:**
> physfs.h: No such file or directory
That's the clue. Install physfs. And see [pkgbuild script](http://aur.archlinux.org/packages.php?ID=11923) for installation clues.

It looks like Debian [mangles and splits the name](http://packages.debian.org/search?keywords=physfs&searchon=names&suite=all&section=all) into libphysfs-dev and libphysfs.

---

### Post by bobmatino17 on 2009-02-06
i compiled it fine and when i tried to run it got...

```
tuxiscool@tuxiscool-desktop:~$ cd /home/tuxiscool/Desktop/d1x-rebirth_v0.55.1-src
tuxiscool@tuxiscool-desktop:~/Desktop/d1x-rebirth_v0.55.1-src$ ./d1x-rebirth-gl
Error: Could not find a valid hog file (descent.hog)
Possible locations are:
        $HOME/.d1x-rebirth
        /usr/local/share/games/d1x-rebirth/
        In a subdirectory called 'Data'
Or use the -hogdir option to specify an alternate location.
Error: Could not find a valid hog file (descent.hog)
Possible locations are:
        $HOME/.d1x-rebirth
        /usr/local/share/games/d1x-rebirth/
        In a subdirectory called 'Data'
Or use the -hogdir option to specify an alternate location.
tuxiscool@tuxiscool-desktop:~/Desktop/d1x-rebirth_v0.55.1-src$ 

```

---

### Post by donkyhotay on 2009-02-06
You need to copy the .hog (data) files from a descent CD in order for it to run correctly. If you don't have one you can get the data files from the demo version and use that but then you're limited to the trial of course.

---

### Post by bobmatino17 on 2009-02-07
also i used the command
```
locate *.hog
```

and got

```

/usr/local/games/Descent3/d3-linux.hog
/usr/local/games/Descent3/d3.hog
/usr/local/games/Descent3/extra.hog
/usr/local/games/Descent3/extra13.hog
/usr/local/games/Descent3/ppics.hog
/usr/local/games/Descent3/missions/d3voice1.hog
/usr/local/games/Descent3/missions/d3voice2.hog
tuxiscool@tuxiscool-desktop:~$ 
```

---

