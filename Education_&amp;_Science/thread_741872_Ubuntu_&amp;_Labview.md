---
title: "Ubuntu &amp; Labview"
date: 2008-04-01
forum: Education &amp; Science
---

### Post by cside on 2008-04-01
Hi all

I am working for a research institute and our main controls are written in Labview - don't get excited. We are using LV 6.1 yes it's very old and it is NOT an option to upgrade Labview.

Currently I am running Ubuntu 6.06 LTS, I think anyway it was the last LTS. There might be an option to upgrade to the new LTS.

I am really wanting to move away from Windoze and I am having success albeit frustrating, and now it is time for me and Labview to fight it out. I have successfully installed the packages and I see them in Synaptics package viewer but I can not run labview. I have tried running labview from the /usr/local/lv61 directory and tried alt+F2 and typed labview - nothing happens. I guess I should be happy about that at least it does not crash. :)

Any hints tips or tricks that I can try or anybody get this combination of software to work?

Any help is greatly appreciated as long as you don't suggest upgrading LV.

---

### Post by cside on 2008-04-02
Ok, its all sorted out, and yes you can run Labview 6.1 under Ubuntu 6.06. For what it is worth to everyone.

A summary of what I did:
Extracted all .rpm files, installed them using rpm in terminal
They then all showed up under the Synaptic Package manager
When I tried running labview under terminal or from the file browser I got nothing.

IT Dept helped out. 
Ran labview using "./labview" from terminal
found there was a missing "libLVMesaGL.so.3"
created link to this file, I also saw him playing in a conf file - not sure which
and ran LV again
-all working

I am not sure how stable or how good the installation is but at this stage I know it is possible to get everything working.

---

### Post by DrOlaf on 2008-04-02
If the installation files are rpm, you may also be able to convert them to deb using [alien]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien"). I've done that several times (though not with labview) and it has always worked well for me.

---

### Post by cside on 2008-04-04
When I went back to my procedure I see that I did actually use alien.

---

### Post by zoubidoo on 2009-02-21
See here for instructions:
[https://wiki.ubuntu.com/LabVIEW](https://wiki.ubuntu.com/LabVIEW)

Z.

---

### Post by dmitriyp13 on 2009-03-17
I havent tried Labview 6 in a really long time but have recently played around with Labview 8.5.  Basic functionallity works in Ubuntu Intrepid but the biggest thing is the lack of DaqMX support.  Labview crashes when it tries to open any .vi file that has DaqMX code inside.  Hopefully, NI will make an Ubuntu/Debian version soon.

---

### Post by jpkotta on 2009-03-22
[http://www.ni.com/linux/support.htm](http://www.ni.com/linux/support.htm)
> Will National Instruments support other Linux distributions?

At this time, NI has no plans to support the following for Linux:
Non-x86 platforms
64-bit platforms
GNU C Library (glibc) versions prior to 2.2.4
Distribution/version combinations other than those specified above

Most of those are understandable albeit disappointing, but no plans for 64-bit?  64-bit is no longer gee-whiz bleeding edge new tech, and it's starting to get to the point where you need it in some common use cases.

I've never used LabVIEW or DAQmx on Linux, but I'm assuming that they only give you binary drivers for DAQmx.  If this is the case, you have to use exactly the same kernel as the supported distros.  If they do something like NVidia's 3D driver or give you source, you probably can get by with using a similar (e.g. same release) kernel.

---

### Post by Royal Virgo on 2010-05-30
HI GUYS,

I Have downloaded labview 8.5 , as i didnt knew much about ubuntu i downloaded the version for windows. It was 3.5 Gb iso. IS there any way round that i can use this pkg in Ubuntu. I really need Quick answer, becasue i have a project to submit . plz do do tel me what should i do.

REgards

---

### Post by dmitriyp13 on 2010-05-30
> **Royal Virgo said:**
> HI GUYS,

I Have downloaded labview 8.5 , as i didnt knew much about ubuntu i downloaded the version for windows. It was 3.5 Gb iso. IS there any way round that i can use this pkg in Ubuntu. I really need Quick answer, becasue i have a project to submit . plz do do tel me what should i do.

REgards
The only way to POSSIBLY make it work is to use wine. But its a long shot.

---

### Post by Royal Virgo on 2010-05-30
i tried that but it shows some unknown eroor while loading instalation files:(

---

