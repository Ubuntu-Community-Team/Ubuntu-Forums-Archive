---
title: "Creating Image With Existing Settings"
date: 2014-12-19
forum: Desktop Environments
---

### Post by zedex2 on 2014-12-19
Hi, 

I am using 14.10 on Virtual Box with few required apps installed + 1 that i have created which has DB setup and other configurations. 

I want to give this to other user to try it out, but sending docs is not a solution as there are many steps and lot of things could go wrong. So how can i create image of my existing setup and give it to user. so user will only have to download and run it in VM and everything would be setup up already.

I hope i have made it clear, let me know if more information is required.

Thanks...

---

### Post by TheFu on 2014-12-19
Doesn't virtualbox have an export appliance option?  File --> Export Appliance?
That should create 2 files that can be imported into other virtualbox installations.  One has the VM settings and the other has the actual VM file (really the OS virtual disk).  Having the correct settings is important.
Also, if you want to give the image away, using DHCP for networking and documenting the userid and login will be needed. Most desktop settings are per userid, not system-wide.

Scripting the install of programs and settings really shouldn't be too hard. For places with Linux installed already, this would be much preferred over distributing a 8-10G VM appliance.

---

### Post by ajgreeny on 2014-12-19
> **TheFu said:**
> Doesn't virtualbox have an export appliance option?  File --> Export Appliance?
That should create 2 files that can be imported into other virtualbox installations.
^^^ As above.

Also, your current VirtualBox VM will be an archive like file called **name.vdi** with name being whatever you called it when you installed it in VB.  It sits in a sub-folder of a main folder in your home called "VirtualBox VMs" if you used the defaults when installing.
Give that large file to your other user and I think it should open in his VB with no major difficulties, other than perhaps ownership problems, but I am not sure about how that is dealt with in a VM.

---

### Post by zedex2 on 2014-12-20
Thanks guys, i will give it a try...

---

