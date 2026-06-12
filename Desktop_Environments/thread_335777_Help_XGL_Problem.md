---
title: "Help XGL Problem"
date: 2007-01-10
forum: Desktop Environments
---

### Post by aslambilal on 2007-01-10
Hi, I just got ubuntu today and have been trying to get xgl on, here's the error i receive when i type

> aslambilal@aslambilal:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12 is to be installed
E: Broken packages
aslambilal@aslambilal:~$ 


Now, i went to packages.ubuntu.com and got the libc6 and reinstalled and i recieved this same error. Any idea what i should do?

---

### Post by vlad.b on 2007-01-11
If you are using the latest version of ubuntu "Edgy Eft" with all the updates. You should have the latest X.org installed. XGL-Server shouldn't be necessary as X.Org to my understanding supports it already. Just get the nvidia driver, and a few extra beryl related packages. Here is a guide that I found very helpful. I am assuming you are using an Nvidia Chipset. 

Their server is down for the moment, but it should be back up soon. 


[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft)

---

### Post by lupine_nickt on 2007-01-11
This smells like the installation of a feisty package on an edgy install.

Can the OP confirm?

xF,

...Nick

---

### Post by jem7v on 2007-01-12
Personally, I would recommend AIGLX instead of XGL, because AIGLX has better support in the most recent Xorg, to the best of my knowledge.  Also, it sounds like it's the better long-term solution.  More reading here that might clear a bit of that up: [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

---

### Post by zanfur on 2007-01-14
I'm experiencing the same problem, on a PPC PowerBook G4.  Comparing it against my ThinkPad T60, I see that the powerpc packages require libc6 >= 2.5-0ubuntu1, while the i386 versions require libc6 >= 2.4-1.  The latest version in Edgy is 2.4-1ubuntu12 (powerpc) and 2.4-1ubuntu12.1 (i386).  Looks like the packages were compiled on a Feisty box?

I attempted to use apt-build to just build it for my Edgy box, but it yelled at me about a missing dist-clean target.

---

