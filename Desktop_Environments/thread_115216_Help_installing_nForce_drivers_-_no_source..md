---
title: "Help installing nForce drivers - no source."
date: 2006-01-10
forum: Desktop Environments
---

### Post by mr_chippy on 2006-01-10
Hi,

I'm not having much luck on the kubuntu.org forums, generally being told "use the search function" (which isn't really helping).. I'm very new to Linux and I'd appreciate a simple answer, even if my questions are stupid. Cheers.

Basically I want to install drivers for my nForce2 mobo and new drivers for my GeForce FX 5900. I have the packages from the nvidia site but both need the source code to recompile the kernel. I can't work out what packages I need to install to get this on my system.

Also, I've seen through my searching that more problems can occur after this: incorrect versions of compilers and such. So basically, does anyone know of or would be willing to give me a quick/simple guide to doing this? How to fix the common problems that generally seem to occur for people.

Many thanks.

---

### Post by Tuf on 2006-01-10
I am a Linux n00b also but I think if you will download the Linux headers for your kernal (available on synaptic or aptget).  I doubt that is all there is to it but it will go along ways to getting you where you are wanting to go.

I havent had much luck getting questions answered unless the answers are to be found in some of the "how to's" posted by the really knoweledgable users.

There is tons of Info on the wiki site and there is also alot of really sharp helpful people on the gentoo site.  I like the conveinence of Kubuntu but I am leaning towards Gentoo just because of the better documentation and there are superb tutorials. Too bad most of them dont apply to Ubuntu.

Dont get me wrong though, it would take a new user quite awhile to get to the point the Ubuntu CD takes you but I think you would understand the OS better the other way.

---

### Post by mr_chippy on 2006-01-10
Initially I had the wrong GCC version.. I've done that and changed the CC variable to GCC 3.4.. now it says I don't have the source.

I have a folder called /usr/src and below that I was expecting a /linux folder but I don't, I have an archive called linux-source-2.6.12.tar.bz2 and a folder called linux-headers-2.6.12-10. I don't seem to be able to open the archive. In synaptic I can see kernel source packages for about 4 different versions but not mine, so I'm a bit stuck now.

---

