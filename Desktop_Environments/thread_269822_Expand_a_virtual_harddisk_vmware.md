---
title: "Expand a virtual harddisk vmware"
date: 2006-10-02
forum: Desktop Environments
---

### Post by distroman on 2006-10-02
I got VMware Server 1.0.1 installed. 

What I have found so fare is that I need to use vmkfstools from the host.

vmkfstools -X 10GB VirtualDiskToBeChanged.vmdk

Then in the guest system use qtparted to expand the harddisk.

I have only seen vmkfstools mentioned with ESX.

Are vmkftools included in VMware Server 1.0.1?
Is it in the Add-on Management for VMware Server?

If not, is there a way to do it?

edit

It's vmware-vdiskmanager for VMware Server.
Works fine, so all is good.

---

