---
title: "Ubuntu Herd 2 - i386 Desktop CD"
date: 2007-01-14
forum: Development CD/DVD Image Testing
---

### Post by luca.mg on 2007-01-14
Hi there, I do not have a bug number as I cannot install on a Tyan 2466 mobo (Amd 760 MP - twin Barton) with a PCI Via VT6420 SATA RAID controller and a couple of Seagate hard disks. At boot time the hard dives are not found, but still the software keeps searching for disks for a bunch of minutes; after a while the desktop cd boots into the live Ubuntu and the disks are not available for mounting. I have to say that I attempted a Fedora Core 6 test drive when it came out and I have had the same problem: googling around I came to the conclusion that the Via sata kernel module it's not working properly since the 2.6.18 kernel release; is this true? What is the kernel shipped with Herd 2? Any chance for a fix? 

With regards Luca

---

### Post by pochu on 2007-01-14
Herd 2 has the 2.6.20-rc4 kernel.

Please, report a bug (search first for duplicates) at Launchpad, and attach the logs that may help.

Regards
Pochu

---

### Post by luca.mg on 2007-01-16
Thank You Pochu for answering me, this bug has already been submitted to the kernel team (with no outcome), see 
[http://bugzilla.kernel.org/show_bug.cgi?id=7625](http://bugzilla.kernel.org/show_bug.cgi?id=7625) and also [http://bugzilla.kernel.org/show_bug.cgi?id=7415](http://bugzilla.kernel.org/show_bug.cgi?id=7415) do You think I should point it to the Ubuntu developers as well? 

Thanks Luca

---

### Post by pochu on 2007-01-16
Yes. Report it at Launchpad, and once it has been reported, you can point it to the upstream bug.

Report it and if you don't know how to point it, I'll do it and tell you how to do it.

Regards
Pochu

---

### Post by luca.mg on 2007-01-17
Ok this is it [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80297](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80297) in the meanwhile I downloaded the Feisty 2.6.20-5 kernel and istalled it and still no way to boot, I hope a fix will be included in the next stable kernel release. Please let me know if I'm supposed to take further action for the bug report. 

Best regards Luca

---

### Post by pochu on 2007-01-17
That's good at the moment. But someone may ask you to explain better the problem, or to attach logs, or something else. Then, please, help them in order to solve this issue.

Regards
Pochu

---

