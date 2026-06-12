---
title: "lxdoom not working"
date: 2005-04-24
forum: Gaming &amp; Leisure
---

### Post by spiderworm on 2005-04-24
hey all,

hoping you can help me figure out what's up with lxdoom.  when I try to play it I get:

LxDoom v1.4.4 ([http://lxdoom.linuxgames.com/](http://lxdoom.linuxgames.com/))
lxdoom: z_zone.c:226: Z_Init: Assertion `32 >= sizeof(memblock_t) && (4*1024*1024) > (128*1024)' failed.
Aborted

There is some information about my system here:
[http://hwdb.ubuntu.com/?xml=d196cb6c6324ea0833040a8e68816c7d](http://hwdb.ubuntu.com/?xml=d196cb6c6324ea0833040a8e68816c7d)

Thanks in advance for your help.

spiderworm

---

### Post by spiderworm on 2005-05-05
*bump*  ](*,)

---

### Post by spiderworm on 2005-05-29
* bump *

---

### Post by scunc_dvl on 2005-12-21
Googled up the exact same error and got this post. From all the tinkering getting the other doom port (prboom) working, I gave up on it. This and the 64-bit badram patch I'll just wait on :P

Got this link with another search, seems X11 may be to blame--I suspect for both doom ports.
[http://ubuntuforums.org/showthread.php?t=74373]("http://ubuntuforums.org/showthread.php?t=74373")

---

### Post by matthewcraig on 2007-11-28
Based on the look of the error, I suspect the lxdoom package does not support AMD64 architecture.  Package should be updated or removed from the 64-bit repository.

---

### Post by disturbedite on 2007-11-28
lxdoom has been dead for a long, long time afaict.  please use a newer doom source port.  i would recommend skulltag.  there is even an ubuntu download available on the st website.

---

### Post by matthewcraig on 2007-11-28
Maybe we should get lxdoom out of the repository and put skulltag into it...

---

### Post by disturbedite on 2007-11-28
@ matthewcraig
thats the best idea i've heard in a while.  wish it would.  there is an ubuntu build (tar.gz/precompiled binary) available for download on the st site tho, it should be easy to make into a deb package...
maybe someone should request it officially.  how does one do that?  file a bug on launchpad?

---

### Post by matthewcraig on 2007-11-29
A bug on launchpad would be a great start.  I think you use a tag of "Wishlist" as a priority.  Post the bug # here and I'll subscribe to voice support!

---

### Post by disturbedite on 2007-11-29
oh thats right, i totally forgot.  (i just recently started filing bugs on launchpad).  i think i'll do that.

(one of the possible problems is that skulltag is not released under the gpl and isn't open source, tho its free).

how do i mark it as "wishlist"?  i can't figure that out...

[https://bugs.launchpad.net/ubuntu/+bug/172871](https://bugs.launchpad.net/ubuntu/+bug/172871)

---

### Post by matthewcraig on 2007-12-01
Looks like it was marked correctly as Wishlist.  I subscribed, showing my support.... Although, I checked their website, and I did not see a 64-bit version.  :(

---

### Post by disturbedite on 2007-12-01
i didn't know how to do a few things when filing a bug, but someone else was kind enough to do it for me.  apparently to make it wishlist, you just put a tag that says wishlist.

i don't know if there is a 64bit version of st, i'm still on 32bit.  i could ask at the forum tho, as i know the guy that maintains the ubuntu build.  he also makes the freebsd build.  i could ask him if he could make a 64bit build, assuming he has access to a 64bit machine.  i'll ask him now and report back.

UPDATE:
ok, i asked him, his name is Torr on the forum.  he said that he isn't even sure if zdoom (which is what skulltag is based on) even compiles on 64bit.  and even if it does, he can't make a 64bit build cuz he doesn't have or have access to a 64bit machine.  and the sound library it uses (fmod 3.75) doesn't even have a 64bit version of the library (if i understood him correctly).  so sorry...

---

### Post by matthewcraig on 2007-12-01
If these are open source software packages, then they can all be "corrected" for 64-bit use.  It's just a matter of defining and using the varaibles and libraries in a way that will work on both architectures.

Actually, a quick Google search shows someone wrote a presentation on that very subject of porting Doom to 64-bit architectures: [http://developer.amd.com/assets/AMD_GDC_2005_Mike_Wall.pdf](http://developer.amd.com/assets/AMD_GDC_2005_Mike_Wall.pdf)

---

### Post by disturbedite on 2007-12-01
if you read the bug report i made you'd know it isn't open source.  and considering that its (obviously) certainly not released under the GPL.  so i don't think its that simple.

i conversed some more with the dev and here is what he said:
 				> I searched through the ZDoom forums and it seems that you can't compile ZDoom under 64 bit because of FMOD. But shouldn't it be possible to just use the 32bit binaries?
and i told him i don't know.  so i guess you could try...

(p.s. as i said before, the reason he is talking about zdoom is cuz skulltag is based on zdoom).

---

