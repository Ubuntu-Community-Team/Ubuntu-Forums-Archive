---
title: "Full story on 2.6.15, udev and Breezy?"
date: 2006-01-11
forum: General Help
---

### Post by MikeN on 2006-01-11
Hi,

As stated on [http://wiki.kernelnewbies.org/LinuxChanges](http://wiki.kernelnewbies.org/LinuxChanges) and on several places on this forum udev support in the kernel has changed as of kernel 2.6.15. This means that for full compatibility you need at least udev 071. Since Breezy ships with udev 060 this version is not fully compatible with the new kernel.

What I've not yet found on the net is a full overview of the impact of these changes. Sometimes I _do_ want to upgrade the kernel to newer versions, and I would like to know what will break when I upgrade to 2.6.15 with an old udev. Will the system still boot? Will the dev nodes get setup correctly at boot? Will hotplug still work (not that I need it)

Could somebody please give some more information abou this? Thanks in advance.

---

### Post by nocturn on 2006-01-11
[QUOTE=MikeN]Hi,

As stated on [http://wiki.kernelnewbies.org/LinuxChanges](http://wiki.kernelnewbies.org/LinuxChanges) and on several places on this forum udev support in the kernel has changed as of kernel 2.6.15. This means that for full compatibility you need at least udev 071. Since Breezy ships with udev 060 this version is not fully compatible with the new kernel.

What I've not yet found on the net is a full overview of the impact of these changes. Sometimes I _do_ want to upgrade the kernel to newer versions, and I would like to know what will break when I upgrade to 2.6.15 with an old udev. Will the system still boot? Will the dev nodes get setup correctly at boot? Will hotplug still work (not that I need it)

Could somebody please give some more information abou this? Thanks in advance.[/QUOTE]


It is not recommended to fit Breezy with a newer kernel, but if you want to test the lastest-and-greatest, why not try the Dapper development version?

---

### Post by MikeN on 2006-01-11
Thanks for your reply :)
The install is for server production use, and of course I can't run the unstable tree on a server. However I do want some kernel upgrades. For instance 2.6.14 contains a fix for the AMD Dual-core procs timer and maybe .15, .16 etc. bring a fix like that, that I really need. Atm this is not the case, but I want to be prepared :)

---

### Post by Viro on 2006-01-11
If the kernel is the only thing you want, is it unsafe to just compile the source that you get from kernel.org? That's what I normally do if I want an up to date kernel.

---

### Post by MikeN on 2006-01-11
The whole point is udev support changed in 2.6.15 and you probably can't simply compile a new kernel from kernel.org and install it. That's what the whole topic is about :)

---

### Post by ikarus9999 on 2006-01-14
Hi

I've recently upgraded to kernel 2.6.15 on my Breezy laptop. 
To answer your questions.

 - Yes, the system still boots up normally. 
 - You could get a few problems with hotplugging and probably same dev nodes are missing. (I had a problem with my synaptic touchpad. The event0/1 nodes were missing.) 

Apart from that everything works normally.

What I've done is upgrading also udev including all depending packages from dapper rep. Since then everything works like before. The only thing is that automount of usb devices doesn't work anymore as this would require the new hal package from dapper. However, this has so many dependencies that I won't risk updating this as well.

I hope I could help you. If you want some more info let me know.

---

### Post by qbits on 2006-01-14
Hello you volunteers ;)

I also use the 2.6.15 with Breezy. But I took the rather hard way: grabed a vanilla kernel and patched it with -ck1. Using the original udev package the new kernel booted but was not quite usable: pppoe was not working - I cant live without ;). So I installed a rather new udev package (including dependencies) from the Dapper repo and now everything is working fine!!!!!

Caveat#1: The new udev package conflicts with hotplog -> remove hotplug solves the problem.

Caveat#2: Now I am *not* able to boot any original Ubuntu kernel as they insist on the old-udev/hotplug combo. So what? Never change a running system...

---

### Post by MikeN on 2006-01-15
Well, what I've done now is just compile a new kernel without any hotplug support. This eliminates the whole udev stuff and uses a static dev, which works fine :)
Thanks for your help guys.

---

