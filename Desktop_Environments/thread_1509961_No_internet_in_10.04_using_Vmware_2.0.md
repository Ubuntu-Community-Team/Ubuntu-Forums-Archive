---
title: "No internet in 10.04 using Vmware 2.0"
date: 2010-06-14
forum: Desktop Environments
---

### Post by CorvetteFan86 on 2010-06-14
Hello all,

I am running Ubuntu 10.04 64-bit in a VMware 2.0 to see if I want to move from 2003 to it. Currently I did a fresh install using "NAT" and when I try to get on the Internet it says it cannot connect. The weird thing is I am able to ping google.com just fine. I also tried bridged and get the same result. Any help would be greatly appreciated.

Thanks in advance,
Thomas

---

### Post by jldoll on 2010-06-14
VMware 2.0 seems kind of old. I'm on 7.X, which is the only version I've used to date. Do you see two arrows in the upper right menu bar? If not, use may need to go to Network Connections and manually connect Auto etho. I think I had to do that the first time, then the system remembered. Also, if 2.0 is old, maybe the correlating VMware Tools package doesn't support newer versions of Ubuntu. I've found Ubuntu support and solutions in the VMware forums, so you can try that as well.

---

### Post by jldoll on 2010-06-14
Clarification: References to menu bar are the Ubuntu menu bar, not VMware.

---

### Post by CorvetteFan86 on 2010-06-15
Thanks for the reply. I am running Vmware Server version 2.0. I have indeed tried reinitializing the eth0 adapter to no avail.

---

### Post by CorvetteFan86 on 2010-06-15
Fixed the issue! I run MAC filtering at my house so: Changed NIC back to bridged then put in the "virtual NIC" MAC in my router and then it worked just fine.

---

