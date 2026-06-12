---
title: "Vostro 1400: HDD problem when installing ubuntu 7.10"
date: 2007-10-30
forum: Dell  Ubuntu Support
---

### Post by bihax on 2007-10-30
My laptop Dell Vostro 1400 with Core 2 Duo T7300, 2gb of ram, 120GB of HDD, the 8400M GS, and the Dell wireless. 
I make a Ubuntu 7.10 clean installation. My HDD has 3 partitions (35GB + 40GB + 15GB = 90 GB). When I use Ubuntu 7.10 LiveCD, I can see all partitions & access them normally, but not when installing. When I choose "Manual" install method, the installation wizard show that my HDD is not partitioned yet (That means my HDD has only 1 partition). :confused:
Can you help me???????

---

### Post by dacap06 on 2007-10-30
Have you tried the alternate install CD instead of doing an install from the Ubuntu Live CD?

---

### Post by professor fate on 2007-10-30
Hello,

I can't help you with that problem, but I am working with the exact laptop, so if you have any other issues...give me a yell.

---

### Post by linusr on 2007-10-31
I have vostro 1500 & exactly same problem. Existing partition not rrecognised by installed.

Earlier i tried with Ubuntu 7.04  Live, alternate cd  with no help.

Now tried kubuntu 7.10 same issue.:(

Need some help as well. Any bug in installer.

---

### Post by linusr on 2007-10-31
> **linusr said:**
> I have vostro 1500 & exactly same problem. Existing partition not rrecognised by installed.

Earlier i tried with Ubuntu 7.04  Live, alternate cd  with no help.

Now tried kubuntu 7.10 same issue.:(

Need some help as well. Any bug in installer.

I wonder how pclinuxos got installed and I noticed all my partitons are 'primary'

---

### Post by linusr on 2007-10-31
> **dacap06 said:**
> Have you tried the alternate install CD instead of doing an install from the Ubuntu Live CD?

alternate doesn't work either

---

### Post by linusr on 2007-11-03
Any help how to proced furthur or debug will be appreciable.

I'm clueless here.

---

### Post by linusr on 2007-11-05
> **bihax said:**
> My laptop Dell Vostro 1400 with Core 2 Duo T7300, 2gb of ram, 120GB of HDD, the 8400M GS, and the Dell wireless. 
I make a Ubuntu 7.10 clean installation. My HDD has 3 partitions (35GB + 40GB + 15GB = 90 GB). When I use Ubuntu 7.10 LiveCD, I can see all partitions & access them normally, but not when installing. When I choose "Manual" install method, the installation wizard show that my HDD is not partitioned yet (That means my HDD has only 1 partition). :confused:
Can you help me???????

Any Buffer IO error while loading live cd?

---

### Post by Raxa JD on 2008-04-11
Might be a possible cause of SATA Hard drive? :confused:

Let us know if anyone comes up with a solution to this.

---

### Post by Ryadt on 2008-04-11
Hi 
go in bios in onboard devices (or something like that) disable flash module. then ata drives switch from ahci to ata..
this should work.
hope that helped..

---

