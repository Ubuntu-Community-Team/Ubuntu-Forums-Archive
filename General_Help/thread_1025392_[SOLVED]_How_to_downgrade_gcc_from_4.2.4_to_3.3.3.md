---
title: "[SOLVED] How to downgrade gcc from 4.2.4 to 3.3.3"
date: 2008-12-30
forum: General Help
---

### Post by lidengdeng on 2008-12-30
Hi guys. 
I met a problem when trying to compile a sourcecode. The gcc version of my ubuntu8.04 is gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu3).

The sourcecode could run properly in another machine whose gcc version is g++ (GCC) 3.3.3 (SuSE Linux).

So how could I downgrade my gcc from 4.2.4 to 3.3.3. I have tried to replace the gcc4.2 by gcc3.3 in Synaptic Package Manager. But it does not work. 

Any help? thanks.

---

### Post by cmnorton on 2008-12-30
What you want to do depends on which version of gcc that was installed. You cannot just downgrade the C compiler, without consequences. There are kernel and CRTL dependencies on the installed C compiler.

I believe you can install 3.3.3. You would have to install it and its libraries, and then point to those in a separate environment file. But do not fiddle with your existing gcc, if it is indeed 4.2.4.

---

### Post by lidengdeng on 2008-12-31
Thanks.
I got your points.

I installed 3.3.3, and then I pointed it to gcc-3.3 when I using it.

---

