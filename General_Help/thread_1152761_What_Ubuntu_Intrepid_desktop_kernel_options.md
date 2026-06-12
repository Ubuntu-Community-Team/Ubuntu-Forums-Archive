---
title: "What Ubuntu Intrepid desktop kernel options?"
date: 2009-05-08
forum: General Help
---

### Post by rainerb on 2009-05-08
Greetings,

what are the standard options set in the standard, Ubuntu desktop kernel? PAE=OFF, pre-emptive multitasking = ON, etc....?


I couldn't find a complete listing of all options on this forum, and preciously little about kernel compilation generally. If I am on the wrong forum, then I am sorry - please give me a poniter to the right place!

Background: I want to install a Physical Address Extension (PAE) aware kernel to get access to more RAM, but I want to stick to the standard desktop kernel in all other aspects, and not use the server kernel. It some aspects it seems to be sub-optimal for home desktop use.

This is what I found about using more RAM:

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

But neither of the two alternatives is what I am looking for.


Also, I do not want to go 64-bit because of possible compatibility issues with NVIDIA, CUDA, etc. We are using this computer as our family "office computer" and I feel that switching to full 64-bit would upset the tranquility of the current setup.

Any help in getting the standard options of the Ubuntu 8.10 desktop kernel would be appreciated. Along with other compilation advice, if anything comes to mind.

Cheers,
Rainer

---

### Post by dcstar on 2009-05-08
> **rainerb said:**
> 
what are the standard options set in the standard, Ubuntu desktop kernel? PAE=OFF, pre-emptive multitasking = ON, etc....?
........
Any help in getting the standard options of the Ubuntu 8.10 desktop kernel would be appreciated. Along with other compilation advice, if anything comes to mind.


All kernel compile options are in the .config file, all of this is explained in the numerous kernel compile HOWTOs that are already available.

---

### Post by rainerb on 2009-05-08
Great, thank you! 

With a quick check I couldn't find the .config file in my /usr/src or any subdirectory there. But there is probably an explanation for that, which I don't know about yet.

Now - forward to learning to compile a kernel.

Have a nice weekend!

---

