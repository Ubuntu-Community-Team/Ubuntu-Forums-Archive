---
title: "Ubuntu 32 or 64 bits on an Inspiron 1420??"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by chiten on 2007-08-08
[SIZE="2"]...Hello! i have an inspiron 1420 with an Intel Core 2 Duo T7100, an i know that this processors have support for 64 bits (not native like AMD). Does anybody know wich distro will have a  better performance, if the 32bits or 64bits, with this kind of processors??[/SIZE]

---

### Post by syssyphus on 2007-08-08
I am guessing that 64 will have better performace, but 32 will have fewer "issues" such as streaming video / etc.

but I was going to ask the same question, since I may get the same model / cpu you have.

---

### Post by EXCiD3 on 2007-08-08
Yes, 64-bit will have better performance, while 32-bit has better compatibility. Flash player doesn't work with 64-bit, but can be "hacked" into working, however these things don't always work. I would recommend 32-bit if you are a new users as you will have less trouble install applications.

---

### Post by chiten on 2007-08-08
ok..thanks!!...i have Ubuntu 64bits on a Athlon3000+ and didn´t have problems with streaming, i had problems only with flash plugin, so i´ve installed a 32 bits browser...i recomend to use "Automatix" to install essential programs...
[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by kuja on 2007-08-09
The one major issue you'll run into apart from anythin xg you might normally run into is that if you reinstall, you won't be getting any of the patches that are installed by default on the new dells. Otherwise I probably would have installed Kubuntu Feisty x86_64 myself.In other words I'm holding out for Gutsy, which **should** have the issues fixed. I think.

---

### Post by ticklecricket on 2007-08-09
I am currently posting from my shiny new 1420 running the 64 bit version. I like the 64 bit version and compatibility isn't really a problem. (I do reccomend automatix in this instance) 

HOWEVER, The Feisty live install cd DOES NOT WORK on the new santa rosa chips (which is what you have installed). So, you have to use the alternate install cd to do a fresh install of x86_64. But, when you install it, x will be broke, so you need to update the kernel. There's a GREAT how-to in this forum, but you have to be comfortable with the shell, know what your doing and have a flash drive and an hour or two of free time. You're also going to have to fix a small handful of hardware issues when you get the install working. Fortunately, all the issues are listed at the dell linux wiki and they have simple solutions listed. It takes at most ten minutes to fix those issues.

If you know what you're doing and you have the time, I say you do it. Just make sure you don't erase the partitions put on the disk from dell. That way you can reinstall the 32 bit version from the disk if you get stuck halfway through.

---

