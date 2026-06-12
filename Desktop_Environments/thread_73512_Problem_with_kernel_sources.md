---
title: "Problem with kernel sources"
date: 2005-10-09
forum: Desktop Environments
---

### Post by Eleka on 2005-10-09
Helo friends!

I'm tring to compile a application and a module (ndiswrapper) that recquieres the kernel-source installed.

I installed the linux-source-2.6.12 package from aptitude, and following the isntructions for the ndiswrapper isntallation, I create a symbolic link in /lib/modules/2.6.12-9-686/build to the source code, but when I run the "make" to ndiswrapper, it say me that in /lib/modules/linux ..../build isn't a linux source code ... I list the /usr/src directory and I have a linux-source-2.6.12.tar.bz2 file ... must it be a directory? I make this work very easy with the 2.6.10 kernel, but I've upgraded to this version and I can't make it ...

Can you help me?

---

### Post by tehwa on 2005-10-09
Hello Elika,

It's a hard question to answer, since the make errors ndiswrapper can throw at the user are numerous, but subtly different each time.

I have ndiswrapper running fine using resources in the Ubuntu Wiki. [This wiki article]("https://wiki.ubuntu.com/SetupNdiswrapperHowto") comes to mind, and if that can't help you, a search for Ndiswrapper in the wiki should get it compiled pretty quickly.

If none of these resources help you, post the error that is given.

---

### Post by Eleka on 2005-10-09
really thanks!!!

It was easy following this howto. I think that I didn't have some packages necessaries and because it didnt works, but following this, all be ok :D

Very much thanks!!!

---

