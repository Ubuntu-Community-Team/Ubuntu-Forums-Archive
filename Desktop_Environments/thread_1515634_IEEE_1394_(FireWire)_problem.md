---
title: "IEEE 1394 (FireWire) problem"
date: 2010-06-22
forum: Desktop Environments
---

### Post by Johnius on 2010-06-22
Hello:

I just installed Kubuntu 10.04 LTS fresh and was going to move my backup files over when I discover that none of my FireWire ports work.  I have one on my Audigy2 ZS and one on the motherboard.  When I plug in the drive, it powers on and spins, but the OS does not detect it.  It has USB as well.  When I switch interfaces, it was detected immediately.  Has anyone else encountered this?  How do I fix it?  I've found a couple of ancient threads regarding similar issues, but none of them helped.

Thanks in advance.

John

---

### Post by Yarui on 2010-06-22
Have you checked the package manager for firewire related software?  The problem could possibly resolve itself if you just install a firewire package.  I have never messed with firewire, though, so I don't know what else to tell you.

---

### Post by Johnius on 2010-06-23
No dice, but thanks for the offer!  Unless I picked the wrong packages.  I read all the descriptions and picked the base packages.

---

### Post by Johnius on 2010-07-07
Bump

---

### Post by CryNGRoad on 2010-07-26
I have the same problem on Ubuntu 10.04 with a WD MyBook 1TB. USB works fine, but Firewire is not recognized.
This bug report seems to deal with the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548513](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548513)

but I haven't tried patching hdparm yet

<EDIT>
I just installed [hdparm v9.29 from source]("http://sourceforge.net/projects/hdparm/") and now it's working. Admittedly it didn't work on first reboot. It started working after I was tooling around in Synaptic removing some old kernels and residual configs then rebooted a second time. Go figure.

Anyway, it works now and I'm happy.
</EDIT>

---

