---
title: "How to prevent XSERVER from starting...."
date: 2008-12-24
forum: Desktop Environments
---

### Post by mojo_man on 2008-12-24
Hi,

I want to run an UBUNTU box as a server but do not want X Server started since it is a resource hog. How can I disable it from starting upon boot?

Thanks

---

### Post by jpkotta on 2008-12-24
X is started by either kdm or gdm in Ubuntu.  You just have to disable the corresponding init script.  
```
sudo update-rc.d -f gdm remove
```

---

### Post by mojo_man on 2008-12-24
> **jpkotta said:**
> X is started by either kdm or gdm in Ubuntu.  You just have to disable the corresponding init script.  
```
sudo update-rc.d -f gdm remove
```

If I wanted to manaully edit the script which one would it be? I do not find rc.d in /etc. I just see a bunch of directories with names that have a rc.d variant.

I have the following:

rc0.d              
rc1.d              
rc2.d             
rc3.d             
rc4.d              
rc5.d              
rc6.d             
rc.local          
rcS.d

Evrything is a directory accept rc.local and that has nothing in it!
         
Respectfully,

---

### Post by jpkotta on 2008-12-24
All the scripts are in /etc/init.d/.  When booting (or more generally, when changing runlevels), the system looks at /etc/rc?.d/.  Those directories have symlinks to the scripts in /etc/init.d/, and (the symlinks) are named in order of execution.  The command I gave removes the symlinks, not the script.  You can still run anything in /etc/init.d/ by hand.

---

### Post by albinootje on 2008-12-24
> **mojo_man said:**
> Hi,

I want to run an UBUNTU box as a server but do not want X Server started since it is a resource hog. How can I disable it from starting upon boot?

Thanks

After removing gdm or the symlinks in /etc/rc* for gdm, you should remember that the Ubuntu desktop version by default uses network-manager, and network-manager will only become active when someone logs into X (desktop).
Make sure that /etc/network/interfaces contains the valid information for your NIC(s) to become connected to the network they're attached to.

See : 
```

man interfaces

```
for examples and more information.

---

