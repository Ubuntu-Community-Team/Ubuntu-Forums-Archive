---
title: "Error boot Live CD"
date: 2007-04-11
forum: Desktop Environments
---

### Post by gaiterin on 2007-04-11
Hello.
I offered myself to install a Linux friend to him, since its computer with Windows goes terrible (800Mhz, 64Mg ram).

I took the minitower to my house.

But there is a problem: Ubuntu does not start.

Story which I did (Before nothing, to say that all the Live CD of Linux that I have already I installed them in my computer without problem, so I discard that the CD is bad):

1. - I put Live CD of Ubuntu 6.06: It starts, but when it arrives at the point to establish the resolution of screen (appears the mouse), it always is with the brown background, reading of the CD, and the mouse lets work (I hope to that it reads of the CD half an hour to give time him, and or I give it by hung, and resumption).

2. - I ask myself if he will be distro, so I put Xubuntu 6.10: It happens the same.

3. - Will be distro of Ubuntu? I put Mandriva 2007 One: It happens the same.

4. - It is strange to me that it works neither Ubuntu nor Mandriva, and I prove with Knoppix 4.0: It works, but when finalizing the load gives a as simple warning as this: “KDE Crash Handler”. Soon it seems that the system executes the things well (although I proved little, since Knoppix like distribucción does not interest to me). 

5. - I think will be fault of the load from CD? I extract the hard disk of the computer of my friend, I put it in mine, and I install Ubuntu to him 6,06 without problem. I return to install the hard disk to the computer and now yes it gives errors that can be descriptive: When establishing the resolution (I put a simple one of 800x600x16 that works well in Windows) leaves a screen text that says “It failed when initiating servant X (its graphical interface). It seems as if it was not formed correctly Quiere to see exit? SI/NO” And it leaves automatically to the console, without allowing to see the exit me. 
6. - With this error, I look for in forums and [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618) encounter I do those steps, putting driver Vesa, and happens the same.

7. - Miro the BIOS, and I put controller VGA like AGP instead of PCI: It happens the same.

8. - I put to the computer of my friend my graphical card to Him. It happens to him the same.

Could be the problem? The graphical card of my friend is a S3 Trio 3D/2X, and the mother board I do not know it. 

Thank you very much by the help.

Marcos.

---

### Post by Jussi Kukkonen on 2007-04-11
> I offered myself to install a Linux friend to him, since its computer with Windows goes terrible (800Mhz, 64Mg ram).

64MB is not enough to run Ubuntu, or even the installer.

If you really want to, see [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems). Do not expect programs like Firefox or OpenOffice to run (just running the the graphical windows system will be difficult).

My real suggestion: buy more ram: that 800MHz machine would be fine with 256 MB.

---

### Post by gaiterin on 2007-04-11
Thanks by answer!
Ok, I will try put my RAM in the other computer... I will say you...
Marcos.

---

### Post by gaiterin on 2007-04-12
Exactly!
The problem was the RAM memory!
With 128 Mb more, it works.
Thanks very much!
Marcos.

---

