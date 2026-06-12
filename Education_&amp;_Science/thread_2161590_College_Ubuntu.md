---
title: "College Ubuntu"
date: 2013-07-11
forum: Education &amp; Science
---

### Post by infinity.tapan on 2013-07-11
I am Mechanical Engg Post-Grad student at Indian Institute of Technology Bombay. Being in research field(and also OpenSource Community fan for a long time now), using Ubuntu here in campus is almost a pre-requisitive. We have our college repositary which is properly maintained and also the new users have to do few tweaks to setup the internet and also download softwares from repo instead of the net. 

Is there a way to come up with pre-modified version of LTS specific to my college with these minor changes. It would be wonderful if I can add few softwares like gFortran, matplotlib-numpy, maybe OpenFOAM to this version. So the new students have easy time getting used to the OS.

Any tutorial, suggestion would be great

Thanks 
Tapan

---

### Post by Cheesehead on 2013-07-11
That is what preseed files are for: [https://help.ubuntu.com/12.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/12.04/installation-guide/i386/appendix-preseed.html)
The installer uses the list of settings and packages in the preseed files instead of the relevant default settings.
One big advantage of a preseed file instead of customizing-and-cloning a system is that it's easier to maintain across releases.

---

### Post by RichardET on 2013-08-18
Go virtual, or create some bootable USB device with a preinstalled system.

---

