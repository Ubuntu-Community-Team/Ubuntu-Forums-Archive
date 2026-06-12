---
title: "Ubuntu 11.04 64bit is not recommended yet?"
date: 2011-09-11
forum: Desktop Environments
---

### Post by alexei_ on 2011-09-11
I have seen similar questions asked before (for previous versions of Ubuntu).
I would like to know if these issues still valid for 11.04:

1) Flash player is still in Beta for x64.
2) Some drivers may not work properly in x64.

I was using x64 for more then 1 year the main issue -- the system hangs from time to time with the only option -- to reboot.

Is there any way to find what was the root cause of the issues?

Another issue (may be related to previous one) -- after playing several "*.mts" video files any video player (tried totem and vlc) was not able to play ANY video.

I am thinking about going with Ubuntu 11.04 32bits. But I am not sure if my issues will be fixed.

My laptop is Gateway NV5378U (15.6" Laptop AMD Athlon II X2 2GHz 4GB 500GB)

---

### Post by coffeecat on 2011-09-11
Hello, and welcome to the forum.

I'll pick up a couple of your points. I've been using 64-bit versions of Ubuntu for more than a couple of years now without significant issue. Flash was a bit unreliable more than a year ago, but it seems OK now. The version of flash that I have installed now through the repository flashplugin-installer package is 10.3.183.7 which, according to what I found on the Adobe site, is the same version as is current in Windows and MacOS.

I don't know what your hanging problem was. Which release of Ubuntu was this with and did you try the 32-bit version? Are you saying that the 64-bit would hang on you, but not the 32-bit version?

If you have 4GB of RAM, then I'd suggest going with the 64-bit version of Ubuntu. It will be a bit quicker than the 32-bit and the 32-bit version won't support the full 4GB of RAM, unless you install the PAE kernel, which I understand slows things down a bit more.

---

### Post by oldos2er on 2011-09-11
64-bit Flash is still beta, but it's worked well for me. Even when it was alpha it worked better in my opinion than 32-bit flash.

As for drivers, did you have specific hardware in mind? I believe there are some third-party printer drivers that are only available as 32-bit; beyond that I can't say.

The "not recommended" description has a long sad history, long story short it was/is a product of the web site designers, not Ubuntu developers.

---

### Post by ottosykora on 2011-09-11
personally, I was also kind of victim of that message on the website suggesting me rather to take 32bit then x64.

However, on my particular hardware, the 32bit did fine job until 10.10.
Starting with 11.04, the all sorts of problems appeared on the 32bit on my hardware (HP ProBook 6550b, all intel stuf in it)

Installed x64 and world started to look bright again.

Yes, I found software which did not work on x64 at all (not from repository) but those few missing things are not so dramatic now.

Also I found, that which way ever you install the x64 flash, it seems to work well.

---

