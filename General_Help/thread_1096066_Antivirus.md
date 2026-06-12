---
title: "Antivirus"
date: 2009-03-14
forum: General Help
---

### Post by 7raTEYdCql on 2009-03-14
I want to know if there is a Linux antivirus that can remove the Windows Virus'.

---

### Post by Dr Small on 2009-03-14
Remove the Windows viruses where?

---

### Post by Sprut1 on 2009-03-14
At the moment a very similiar thread is going on, if only there was a way to figure out where...

---

### Post by Twitch6000 on 2009-03-14
Wow just answer his question... don't confuse the person :/.

The answer is download clamav or avg.

clam is in the repos and avg is on the avg site.

---

### Post by khelben1979 on 2009-03-14
To answer your question: I don't know, but have you tried running Windows anti-virus with [the Wine program]("http://www.winehq.org/")?

Those anti-virus programs which I have seen for Linux have all used the [ClamAV]("http://en.wikipedia.org/wiki/Clamav") engine and if this is able to detect Windows viruses, well, there you have it, I guess.

---

### Post by hichamroudi on 2009-03-14
I am using Bitdefender. I requested free home user licence key for 450 days from their website. take a look on here:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

By the way,I am not sure whether Linux platform anti-viruses take on account ms windows threats. Who knows, maybe their targets are the few Linux viruses.

---

### Post by mb_webguy on 2009-03-14
> **hichamroudi said:**
> I am using Bitdefender. I requested free home user licence key for 450 days from their website. take a look on here:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

By the way,I am not sure whether Linux platform anti-viruses take on account ms windows threats. Who knows, maybe their targets are the few Linux viruses.

Well, since there are only less than a couple of dozen known viruses for Linux, all of those are either obsolete or created as proof-of-concept, and Linux anti-virus programs are primarily used on mail- and web-servers to prevent passing viruses to Windows computers...  ClamAV and other Linux-based antivirus apps are almost entirely for detecting Windows viruses.

If you're running Windows, AVG is a very good anti-virus/anti-spyware application.  AVG for Linux, however, is a scanner only, and has no capability to remove infected files.  ClamAV can both scan for and remove infected files.  It's a command-line app, but it has several good GUI front-ends, such as clamtk.

---

### Post by lisati on 2009-03-14
> **mb_webguy said:**
> Well, since there are only less than a couple of dozen known viruses for Linux, all of those are either obsolete or created as proof-of-concept, and Linux anti-virus programs are primarily used on mail- and web-servers to prevent passing viruses to Windows computers...  ClamAV and other Linux-based antivirus apps are almost entirely for detecting Windows viruses.

If you're running Windows, AVG is a very good anti-virus/anti-spyware application.  AVG for Linux, however, is a scanner only, and has no capability to remove infected files.  ClamAV can both scan for and remove infected files.  It's a command-line app, but it has several good GUI front-ends, such as clamtk.

If you choose AVG, save yourself some heartache (there are a couple of pitfalls) and read [here]("http://ubuntuforums.org/showthread.php?t=889552")

---

### Post by jflaker on 2009-03-14
> **i.mehrzad said:**
> I want to know if there is a Linux antivirus that can remove the Windows Virus'.

It is called Ubuntu.  Boot from the LiveCD, Start the installer and choose use the whole disk when asked about partitioning and the Windows virus will be gone for good.

But seriously, you can install Clam which is in the repository (SYSTEM>ADMINISTRATION>SYNAPTICE PACKAGE MANAGER then search for clam


Clam should identify and remove almost all known viruses.

---

