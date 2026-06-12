---
title: "Thought I had 64bit 14.04"
date: 2014-06-17
forum: Desktop Environments
---

### Post by Kenkoy on 2014-06-17
Hi folks. I just have a quick question. I downloaded Ubuntu 14.04 LTS from [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

There were only 2 choices available according to the page, a "PC (Intel x86) desktop image" and a "64-bit PC (AMD64) desktop image".

Why, then, did my option, ubuntu-14.04-desktop-i386.iso, turn out to be 32-bit? I have an i5-2500K on an ASRock Z68 Extreme4 board, with Windows 7 64bit running on another partition.

If this isn't 32bit, then why does System Settings > Details report it as such?

It has been quite a process repurposing this system with new components and software. How much funtion and speed will I lose if I decide to just keep this 32bit version? My goals are to run Blender 3D modeler and GIMP, mostly. If it's possible to view online 3D videos with Linux (I have an Nvidia GTX 750Ti card and a 3d-capable monitor), then I'd like to do that as well. I never allow Windows 7 online. He can't be trusted:-)

Thanks for your help here. This has been a learning experience but it's put me terribly behind my required schedule. Cheers!

---

### Post by squakie on 2014-06-17
Don't go by the processor manufacturer as the version to get - it's simply this: 

PC (Intelx86) desktop image  is 32-bit

64-bit PC (AMD64) desktop image is 64-bit

BOTH work on Intel or AMD processors.  You'd need to know a little computer history to understand, but believe it.

So, you have 32-bit because you downloaded and installed the 32-bit version (x86 is the hint).  If you want 64-bit, download the 64-bit version and you'll need to re-install.

---

### Post by LastDino on 2014-06-17
i386 option is the x32 bit version.

AMD64 is the x64 bit version.

I know, the name is misleading, but if your system is x64 bit, use AMDx64 bit version. That name consist AMD for historical reasons, it has nothing to do with something like only supporting AMD, so don't worry.

---

### Post by rahul4557 on 2014-06-17
In 2003
AMD introduced its [Opteron]("http://en.wikipedia.org/wiki/Opteron") and [Athlon 64]("http://en.wikipedia.org/wiki/Athlon_64") processor lines, based on its [AMD64]("http://en.wikipedia.org/wiki/AMD64") architecture which is the first x86-based 64-bit processor architecture.
In 2004
Intel, reacting to the market success of AMD, admits it has been  developing a clone of the AMD64 extensions named IA-32e (later renamed  EM64T, then yet again renamed to Intel 64). Intel ships updated versions  of its [Xeon]("http://en.wikipedia.org/wiki/Xeon") and [Pentium 4]("http://en.wikipedia.org/wiki/Pentium_4") processor families supporting the new 64-bit instruction set.

Source: [Wiki]("http://en.wikipedia.org/wiki/64-bit")

So 64-bit version is called AMD64 because of its AMD64 architecture.

---

### Post by squakie on 2014-06-17
Yep - that's the history portion I mentioned.  The solution is in my original post.

---

### Post by Kenkoy on 2014-06-17
Well, thanks folks for your answers. It wasn't just the misleading names. It was the descriptions that set me in the wrong direction. The one I chose simply said "For almost all PCs." It says nothing about being 32-bit. 

I guess if you include all PCs that still exist including those in recycling centers and thrift shops, then, yeah, almost all PCs are 32-bit. But an average idiot like me would assume it was referring to PCs that most people use nowadays. My 88 year old mother has a machine nearly as modern as mine.

I originally looked up "x86" and found in Wiki that the term includes 64-bit registers. I guess that's not the same "64-bit" we're referring to... I build my own, I repair my own, I just don't know what I call my own!

Well, I'm stuck with 32-bit because work I've promised for people has been on hold for too long. I don't think there will be much difference in speed, anyway, except possibly with Blender.

It's infuriating, but heck, it's free - I'm happy. I appreciate having Linux available and I greatly appreciate your help in this matter. Cheers!

---

### Post by grahammechanical on 2014-06-17
Consider this. 32bit Ubuntu will run on both 32bit and 64bit CPUs because the architecture of the 64bit CPU is backwards compatible with a 32bit OS. But 64bit Ubuntu will only run on 64bit CPUs. The same applies to other operating systems.

So, by downloading a 32bit Ubuntu even though their machine has a 64bit CPU the potential new user doesn't fail to get a working install. Which is exactly what would happen if they downloaded and tried to install 64bit Ubuntu on a 32bit machine. Hence the "for almost all PCs" comment in that download page and also the "choose this if you are at all unsure" message.

---

