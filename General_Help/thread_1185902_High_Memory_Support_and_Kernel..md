---
title: "High Memory Support and Kernel."
date: 2009-06-12
forum: General Help
---

### Post by syntheticz on 2009-06-12
I need to compile a kernel with high memory support for my friend as his new system will have 4GB of RAM and it will be more convenient for him to use a 32-Bit OS. However when I start up xconfig to enable high memory support. It is greyed out and I am unable to enable it. 

Is there any fix for this? 
Thanks

---

### Post by Agent ME on 2009-06-12
What's the need for using a 32-bit OS? There's no need to stay away from 64-bit if the hardware supports it.

I'm not sure about how to make a 32-bit kernel use 4+ gb ram, but I think the ubuntu server kernel can do that.

---

### Post by jerrrys on 2009-06-12
lots of info here

[http://www.google.com/search?q=pae+ubuntu+kernel&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=pae+ubuntu+kernel&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Yellow Pasque on 2009-06-12
Alternatives:
- Use 64-bit
- Use -server kernel
- Don't worry about it (lots of users will struggle to max out 2GB of RAM, even more 3.2GB)

---

### Post by syntheticz on 2009-06-13
The server kernel does have PAE enabled however compared to the desktop it is a stripped down version of the kernel,the system will primarily be a desktop version, as for 64 bit that was my initial course of action however I heard that a lot of programs don't have supported libaries/dependancies for it. So I plan to try and make it as fuss free as possible for the person who is going to be using the OS. 

If theres nothing else to do I will have to use the server kernel.

---

### Post by PmDematagoda on 2009-06-13
Perhaps you could try compiling a stock kernel source and using that? Although that would mean that you or your friend would need to update kernels yourselves, but if you're going to compile the Ubuntu source anyway, that probably won't matter.

---

