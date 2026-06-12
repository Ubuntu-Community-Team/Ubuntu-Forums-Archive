---
title: "Disappearing folders"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Dagonus on 2005-11-17
I've got a TC1000 and i'm using Longrun to take advantage of the power throttling of the Transmeta Crusoe processor. (I know its a hideous processor outside that)

In order to run it I need to:
*  mknod /dev/cpu/0/msr -m 0644 c 202 0
* mknod /dev/cpu/0/cpuid -m 0600 c 203 0 

The problem comes in that only /dev/ exists and not any of the folders beyond it. 

I can create the folders and the files no problem, but after a restart.... Gone.

Why? and how can I make them not get vaporized by the system on restart?

---

