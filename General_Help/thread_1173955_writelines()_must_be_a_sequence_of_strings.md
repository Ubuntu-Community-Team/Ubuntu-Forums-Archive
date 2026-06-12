---
title: "writelines() must be a sequence of strings"
date: 2009-05-30
forum: General Help
---

### Post by yelmo on 2009-05-30
I am trying to install Ubuntu 9.04 with wubi 9.04.
My Vista is in French, the Ubuntu installation via wubi works fine if I use French (default)
However, that is not what I want. I want to installa ubuntu in Spanish, but when I change the language to any other than French in the Wubi window I get the following message soon after the installation process begins:

writelines() must be a sequence of strings

The installation crashes completely. No way to continue.

---

### Post by Shroomsoup on 2009-10-17
Hi, it has been found that this error occurs when you try and change the language on the Wubi installer. To avoid this error you must install Ubuntu with the same language as that of your PC. I found this information [here]("https://bugs.launchpad.net/wubi/+bug/365642"). Hope this helps.

---

