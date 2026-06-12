---
title: "Any decent (working) Doom source port?"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by noerrorsfound on 2007-05-17
PrBoom locks up after a few seconds.
[https://launchpad.net/ubuntu/+source/prboom/+bugs](https://launchpad.net/ubuntu/+source/prboom/+bugs)

LxDoom says
> lxdoom: z_zone.c:226: Z_Init: Assertion `32 >= sizeof(memblock_t) && (4*1024*1024) > (128*1024)' failed.
Aborted (core dumped)

I get this message when trying to compile zdoom 2.1.7:
> Assembling a.nas:                                                     [ERROR]  
nasm -o releaseobj/a.o -f elf -DM_TARGET_LINUX src/a.nas
================================================================================nasm: No such file or directory
make: *** [releaseobj/a.o] Error 99

When following the instructions to compile Doomsday I see this:
> CMake Error: The source directory "/home/nicholas/deng-1.9.0-beta5.1/doomsday" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

---

### Post by hikaricore on 2007-05-17
At the moment the server is down (might be for awhile) but debian/ubuntu packages for Doomsday live here from time to time:

[http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/)

---

### Post by noerrorsfound on 2007-05-18
> **hikaricore said:**
> At the moment the server is down (might be for awhile) but debian/ubuntu packages for Doomsday live here from time to time:

[http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/)
The server was up this morning and I had to leave for school but after I got home it was down again and still is. The packages were for Ubuntu 6.06 so I'm not sure how compatible they would be on 7.04.

I would prefer a version without all the graphical enhancements, anyway. Does anyone else know of another good Doom source port?

---

### Post by DoktorSeven on 2007-05-19
Regarding Doomsday 1.9.0b5.1, they left that one file (CMakeLists.txt) out of the source tarball.  You can download it directly from their CVS ([http://deng.svn.sourceforge.net/viewvc/deng/tags/1.9.0-beta5.1/doomsday/](http://deng.svn.sourceforge.net/viewvc/deng/tags/1.9.0-beta5.1/doomsday/) - click the revision number, then Download at the top, save it under the Doomsday directory). 

Course, from my experience, Doomsday 1.9.0 releases haven't worked very well -- they tend to be sort of buggy, and b5.1 (at least) doesn't even run one of the Final Doom episodes. :(

I've stuck with 1.8.6 regardless of how supposedly buggy it is.  You do need gcc3 to compile it though (**sudo apt-get install gcc-3.4 g++-3.4**, use **CC="gcc-3.4" CXX="g++-3.4" ./configure**).

---

### Post by noerrorsfound on 2007-05-19
I have it compiled but it crashes when trying to run:
```
Segmentation fault (core dumped)

```

---

### Post by disturbedite on 2007-05-19
Yagisan, the guy that made the ubuntu packages for doomsday stopped that a while back.  he won't being doing it any time soon either.  so thats prolly why his site is down pretty often.  i don't think the repos are of any use either any more cuz of that.

---

### Post by hikaricore on 2007-05-19
> **disturbedite said:**
> Yagisan, the guy that made the ubuntu packages for doomsday stopped that a while back.  he won't being doing it any time soon either.  so thats prolly why his site is down pretty often.  i don't think the repos are of any use either any more cuz of that.

I've never had any trouble with his packages and they are still working to this day (on Feisty).

The author of the thread mentioned there is no interest in these packages so I guess it's kinda pointless for me to discuss.

---

### Post by disturbedite on 2007-05-21
i didn't mean his packages don't work, i just meant that they'll be sorta obseleted once newer versions of doomsday are released...

---

### Post by noerrorsfound on 2007-05-21
I thought I had found a solution to my problem when I found a source port called Vavoom, but it has the same issue as PrBoom (freeze/lockup).

I created a thread about it on their forum:
[http://vavoom.heretichexen.com/forums/viewtopic.php?t=1084](http://vavoom.heretichexen.com/forums/viewtopic.php?t=1084)

---

### Post by scunc_dvl on 2007-06-05
Disabling transluscency helped me keep prboom running longer. It still had sound issues though. 

I got zdoom working with some effort. ([http://www.zdoom.org/wiki/index.php?title=ZDoom_on_Linux](http://www.zdoom.org/wiki/index.php?title=ZDoom_on_Linux) got me going once I got past the compile errors.. )

---

