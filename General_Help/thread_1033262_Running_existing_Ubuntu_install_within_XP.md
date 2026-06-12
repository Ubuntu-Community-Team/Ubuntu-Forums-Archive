---
title: "Running existing Ubuntu install within XP??"
date: 2009-01-07
forum: General Help
---

### Post by inspired on 2009-01-07
Hi folks,
I have WinXP Pro and Ubuntu 8.10 installed on a laptop. I have keep XP on there because I use Adobe CS4 for publishing work. I have to use that for now.

I have looked into virtualisation options such as VMWARE and Virtualbox, but I don't like the idea of installing yet another (albeit virtual) OS along with the other two.

What I want to be able to do is access (run) my Ubuntu installation whilst I am using XP for design work.

I read this article with interest:
[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)

It is suggesting a way to do the reverse of what I want to do... this gave me hope.

I will try this out as a way to access my XP install within Ubuntu. But so far I think CS4 will not like running in a virtual environment (too slow, and certain drivers are not hardware specific as far as I can tell, such as the graphics driver).

My question is this:
Is there a way to run a virtualisation of my existing Ubuntu install from within XP and also to run that same existing Ubuntu installation on it's own (as I do now, through dual booting)? I would then use Ubuntu for access my emails, internet, etc. I have not given net access to my XP install as I am fed up with the madness of viruses and firewalls.

With much thanks,

Jonathan

---

### Post by adamlau on 2009-01-07
If CS4 runs well in your XP install, it will run fine within a virtual enviromment under Ubuntu. As a point of reference, I run AutoCAD 2008 on XP under Ubuntu on my ThinkPad T42 without any issues whatsoever. Allocate half your system memory to VMWare, install VMware Tools for drag and drop access between the environments and you are good to go. Do not fear VMWare Workstation for Linux. Yes, it is a large (sized) application and yes, your boot times will suffer, but you will achieve your goal of dynamically switching between two operating systems within a single session. If you plan to choose VirtualBox over VMWare, make sure you go with the commercial version as the OSE version in the repositories is crippled (full screen is locked out, for example). And for the record, OpenSolaris is able to run the full version VirtualBox for personal use.

---

### Post by inspired on 2009-01-07
> **adamlau said:**
> If CS4 runs well in your XP install, it will run fine within a virtual enviromment under Ubuntu. As a point of reference, I run AutoCAD 2008 on XP under Ubuntu on my ThinkPad T42 without any issues whatsoever. Allocate half your system memory to VMWare, install VMware Tools for drag and drop access between the environments and you are good to go. Do not fear VMWare Workstation for Linux. Yes, it is a large (sized) application and yes, your boot times will suffer, but you will achieve your goal of dynamically switching between two operating systems within a single session. If you plan to choose VirtualBox over VMWare, make sure you go with the commercial version as the OSE version in the repositories is crippled (full screen is locked out, for example). And for the record, OpenSolaris is able to run the full version VirtualBox for personal use.

Okay. Thanks for that info. I appreciate you sharing your experience.

I currently have Virtualbox installed (latest full one downloaded from their site). The installation instructions I was finding for VMWARE on Ubutnu 8.10 seemed longed winded and people were reporting mixed results.
Do you find one works better than the other when it comes to running high end apps like autocad and CS4?
I'll revisit attempting to install VMWARE if that's likely to be better.

One more question... can I somehow package up my existing XP installation into an image for VMware and/or VBox?

***For the record... I am still interested to know if it's possible to do what I've asked about... with regards to running my Ubuntu installation from within a virtualisation program on XP.***

With much thanks,

Jonathan

---

