---
title: "How to give ubuntu user the root privilege"
date: 2009-01-23
forum: General Help
---

### Post by micks80 on 2009-01-23
Hi Friends,
I am new to ubuntu and I am trying to connect to an "Ubuntu" server using VMWare Converter and it throws this message:

User name 'myuser' does not have root privileges on the source machine.

I searched the forums and tried few things,like:
I added 'myuser' to the root group but it still throws that error.

Can someone please tell me what needs to be done to give the user 'root' privileges.Since the converted is using 'ssh' to connect, are there any specific 'ssh' related settings that needs to be performed.

Thanks

---

### Post by grndslm on 2009-01-23
I'd figure someday the sudo questions would go away, but I digress...

open a terminal and type:
sudo vmware_command

if you want to run a bunch of super-user commands without typing sudo everytime, type:
sudo -s

if this 'myuser' you're referring to isn't the initial user created at install (the super-user), then login to the SU account and type:
sudo adduser myuser admin

Then repeat either of the first 2 steps above.

---

### Post by micks80 on 2009-01-23
Hi,
I am sorry but you misunderstood my question.

I am trying to connect to the 'ubuntu' virtual machine from a remote windows server using the VMWare Converter. So in this case 'sudo' does not comes into picture at all...

Yes, this is the first user that was created during ubuntu install.

Any help now?
Thanks

---

### Post by Coreigh on 2009-01-23
I think this will be a problem unless there is a command option for VMWare-converter that is for this specific issue. VMW-C is trying to do something on the Ubuntu box that requires superuser priviledges, Ubuntu's security model eliminated the root account in favor of the sudo command (similar to OS X). So you will have to break the Ubuntu security model (very frowned upon) or get some help from the VMW-C community, or opt for a Linux distro not designed around the Ubuntu security model; i.e. one that still uses root accounts.

---

### Post by micks80 on 2009-01-23
Is there any easy way to change ubuntu's security model and give superuser privileges to connect remotely???

---

### Post by Coreigh on 2009-01-23
Like I said it is frowned upon. Yes it can be done but that topic is forbidden on these forums. You will have to visit Google.

I would start with VMW-C first though and ask there if any one else uses Ubuntu and how did they get around the problem. You really don't want to break Ubuntu just to use it.

Best of luck.

---

### Post by micks80 on 2009-01-23
The problem is that the VMC I was using was v3.0 and it did not supported linux, and so I downloaded beta v4.0 which supports linux  kernel >2.4 but now I am encountering this privileges issue.

My whole point is to increase the disk size, so I think I should resort to the command line option i.e.
vmware- vdiskmanager -x 12GB "My harddisk.vmdk"

But after that, I have to resize the partition table manually and I don't have any software or not too used to it. I always used VMC before and it worked like a charm.

So let's see if someone on vmware forums has something for me...thanks a lot for your help!!!

---

