---
title: "Math programs in ubuntu"
date: 2010-07-29
forum: Desktop Environments
---

### Post by katrine_l on 2010-07-29
Hi

I have been using ubuntu for fun along side my vista for a little while now. But now I've had it with vista, it's simply too slow and insecure to use in school. 

But here's my problem, in my math class we use the math programs Mathcad or Mable, but since I'm quitting vista I can no longer use those programs, so does anybody know a good alternative that runs on ubuntu 10.04?

thanks a lot.

---

### Post by 3Miro on 2010-07-29
Some versions of Matcad work well under wine, check out WineHQ forums for details.

Do you mean Mable or Maple. I have never heard of Mable and I couldn't find it on Google. Maple has version for Linux:

[http://www.maplesoft.com/products/system_requirements.aspx](http://www.maplesoft.com/products/system_requirements.aspx)

Most math software has versions for Linux, Matcad is more of an engineering thing and hence an exception.

---

### Post by Mbhiza on 2010-07-29
**Maxima **- this is a regular math program with integrals and stuff
** Octave ** - This is matlab free and Linux version.

---

### Post by 3Miro on 2010-07-29
> **Mbhiza said:**
> **Maxima **- this is a regular math program with integrals and stuff
** Octave ** - This is matlab free and Linux version.

Yes, those may also work.

Octave is very similar to Matlab, but it is not Matlab, just mostly compatible with Matlab. There is separate Matlab for Linux.

Octave and Maxima can probably do everything that Maple does and even more, but school may require Maple specifically.

As far as I know, there is nothing Linux native that can do what Matcad does. Of course, I may be wrong.

---

### Post by QIII on 2010-07-29
While there may be fine Linux alternatives, the operative consideration is whether your work can be done with one of those and presented to the instructor -- who may be expecting it solely in the formats used in the specified software.

If that is the case, I would suggest using the PEUL version of VirtualBox (or another virtualizaton application) to create a virtual machine and install Windows in it -- assuming you have a full retail installation disk and NOT an OEM disk (Microsoft's EULA specifically forbids the use of OEM disks for installing in virtual environments.  Don't violate it.  A contract is a contract, regardless of how badly you might want to "stick it" to Microsoft.).

In the VM, you could run the specified application natively in Windows.

I suggest VirtualBox primarily because it is free.  You can use the PEUL version (which has full USB support), so long as you agree to use it only for personal and not commercial use.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by katrine_l on 2010-07-30
Thanks for your replies everyone. :)
I will take a look at Maxima and Octave, but as I really am very fond of Mathcad, I already tried to run it in Wine. It didn't work very well, the program returns a runtime error and shuts down. Like 3Miro points out, only some of the Mathcad versions runs under Wine, which could be the reason why it isn't working (I'm using Mathcad 14). 

The virtual machine sounds interesting, but will I be able to access files created in there from ubuntu?

---

### Post by QIII on 2010-07-30
Depending on how you set up the VM, you should have access to other shared directories on other drives on your network and vice-versa when the VM is running.

So you can always save the file somewhere where you can get at it from you primary OS.

---

### Post by katrine_l on 2010-07-30
alright I'll try it then, thank you. :D
(btw I have a legal copy of XP which I can use, so no trouble there ;) )

---

### Post by BFris on 2011-03-18
My vote would be for CompPad. Everything else is too much of a hassle. wxMaxima is quite nice. You can get pretty equations. And it has units. But it's easy to make mistakes and get the wrong answer. As a long term goal, I'd still like to learn Maxima because it's so powerful.

CompPad has all of the compelling features of MathCAD: gentle learning curve, natural math notation, and built in graphics. What makes CompPad potentially better than MathCAD is that you can make publication quality papers. 

I'd recommend the 0.3.x branch.

---

