---
title: "Problem with scanner/parallel port"
date: 2006-02-09
forum: Desktop Environments
---

### Post by sitara on 2006-02-09
I have posted this problem several times and see that there are a number of other threads related to the same sort of problem, but I don't see any answers. I would really appreciate it if someone could help me out here!

I have an HP PSC500 printer/copier/scanner. I had some permissions problems getting the printer working, but it is now fine.

The problem now is with the scanner. According to HP's website, I need to use HPOJ, not HPJLIB for this product. I have used HPOJ successfully with the same device on Suse, Xandros and Linspire previously, so I know it can be done!

I have run  "sudo /etc/rc2.d/S19hpoj setup", but get a message "ptal-mlcd failed to start!  Check syslog file for error messages.". The syslog says: "localhost ptal-mlcd FATAL ERROR at ParPort.cpp:48, dev=<mlc:par:probe>, pid=25291, e=1, t=1139479012         Access denied to parallel port!". I don't know where to find the permissions for the parallel port. From what I've read, it should be found at "/dev/parport0" but that file doesn't exist on my system. Kinfocentre can see something called parport0, which has addresses associated with it, but I don't see any way to set permissions there.

Please help! I have got as far as I can go with this problem and it's really critical.

Thanks in advance,

Keith

---

### Post by aul2806 on 2006-02-25
I had some problems with PSC500, too. My solution was:
- downloading 0.9.8 hplip from HP (I don't know whether this was realy necessary).
- added in the /etc/init.d/hplip script in the start function:
   modprobe ppdev . I found that in a gentoo forum. After adding The hp-setup script found the parport and I was able to configure the printer too.
Good luck!

---

### Post by aul2806 on 2006-02-25
sorry I forgot something. The access permissions problem: My solution was to comment out the runAsUser directive in cups configuration:
#RunAsUser Yes

---

### Post by sitara on 2006-03-10
Thanks AUL2806. Seems I was barking up the wrong tree with HPOJ. I added the 'modprobe' to the HPLIP start script and everything worked fine. I have uninstalled HPOJ now and the printer and scanner are still working.

---

