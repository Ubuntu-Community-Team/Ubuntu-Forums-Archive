---
title: "KVM- Bad random disk access performance"
date: 2017-02-14
forum: Fedora/RedHat and derivatives
---

### Post by henriqueps on 2017-02-14
Hello folks.
We're having some troubles with kvm guest performance, and we would somebody could help us.
Actually we are testing KVM running on Ubuntu 16.04 LTS, with Windows guest and MSSQL installed.
The point is, this guest can't even reach 50% of the Vmware guest performance (the configurations are the same, same host, memory, disk, ...)
We're using LVM for storage for guest
For the performance tests we're using HammerDB.


Here are my host configuration (is only for testing proposes):
Dell Poweredge 1950
Disk: 2 x 500GB Sata
Processor: 2 x Intel E5410
Memory: 32GB


Guest configuration
Processor: 8 (host-passthrough)
Memory: 30GB (it was not installed ballon driver)
Disk: 100GB (storaged on LVM volume and with Virtio blk driver)
Network: Installed with Virtio net driver

The performance results are here: [https://docs.google.com/spreadsheets/d/1sQwkUpjnFWuFNWYNlbvaAne3_pLFNHoP3UkNwCl9cy4/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1sQwkUpjnFWuFNWYNlbvaAne3_pLFNHoP3UkNwCl9cy4/edit?usp=sharing)

When I run a simple sequential disk read/write test, the results are beautiful, KVM demonstrates better than VMware
KVM Guest
Sequential write: 110MB/s
Sequential read: 132MB/s
VMware Guest
Sequential write: 100MB/s
Sequential read: 116MB/s
[COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]
There is something that we are missing?
Could you please give us some light?

---

### Post by KillerKelvUK on 2017-02-14
Hi and welcome, Im not shutting the door on your request for support but if you are using CentOS for the host operating system then I'd suggest you might get better support on a CentOS forum.  KVM implementations can vary by distro and the underlying OS configurations certainly do vary by distro.

Things I'd suggest you look at as part of your investigations are...
[LIST=1]
[*]Before even starting a guest ensure your host is properly configured and operating as expected i.e. reviewed dmesg outputs? This could involve any number of kernel parameters/optimisation to ensure linux is making best use of your hardware e.g. interrupts, acpi, iommu etc.
[*]Is the host idling properly i.e. no erroneous process chewing CPU cycles, does the storage perform to the levels expected consistently.
[*]Have you configured KVM properly e.g. the appropriate application of hugepages and other performance factors.
[*]Have you planned and executed your guest configurations properly i.e. CPU pinning with correct pairing of core to thread (if hyperthreading), install all necessary guest tools (looks like you have from your post)
[/LIST]

You haven't said if you're running the guests from the cli using Qemu direct or whether you've installed libvirt?  Plus its always a good idea to post your guest configuration.

I've little experience in running KVM in a production environment so from an experience perspective there are others here who may have a silver bullet to offer you so worth adding the extra details and hopefully someone will catch this and offer you further advice.

---

### Post by QIII on 2017-02-14
*Moved to **Fedora/RedHat and derivatives***

Quite right.  The Ubuntu Forums exist primarily for the support of those using Ubuntu or official flavors.  There may be substantial differences between potential solutions across distros.

You are, nonetheless, quite welcome to post your question here.  I certainly hope someone is able to help you.

Cheers!

---

### Post by henriqueps on 2017-02-14
Ow, sorry man, my bad, I've just written wrong.

Cause actually we are testing both distributions, CentOS 7 and Ubuntu 16.04 LTS, and in both distributions we saw this problem.
So we're searching for the possible answers!!

Thanks for the alert, and sorry for the confusion!!

---

### Post by henriqueps on 2017-02-14
Could you, please, move back to Ubuntu Virtualisation?
I've made a mistake, I'm running Ubuntu 16.04

---

