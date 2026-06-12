---
title: "xen and karmic"
date: 2010-02-09
forum: Desktop Environments
---

### Post by idella on 2010-02-09
As a linux user, I'm in dismay at ubuntu's standing with xen.  I'm in a fresh install of karmic, and I wanted to see what it offered with xen.  I'm trying to find a distro that can match Suse's.  On installing, I look up the packages for xen.  Lots there but something missing.  I just couldn't find a kernel listed  Everything xen but no kernel.

As it happens, I have one for karmic.  I've been in a debian lenny environment for a while doing the same thing.  I  am perplexed at what I find.  To see lenny's shortcomings just check my post on the debian forum.

As for karmic,  Firstly no dom0kernel.  As a gentoo user, I used gentoo's kernel on both lenny and karmic just to get into xen.  lenny's kernel couldn't get into gnome.

Having finally got into xen, I wanted to see the virtual manager at work.  Well.
It looks good in a regular kernel environment.  It cators to qemu and kvm.  As for xen,

The install wizard restricts xen vms to a paravirt form.  This warrants a network device to install.  I used instructions in a magazine article to hook up ftp and the cdrom.  I tried as many permutations as I could muster, but the  install wizzard was never satisfied with the entries.  Can't install vms from virtual manager.

The virtual manager has a help doc.  It's the same help doc I found in lenny.  lenny is about 18 months behind the rest of the linux distro world.  The help doc simply didn't match the newer version of the virt-manager.  I copied and pasted a net source from the help doc into the entry for install source, and it still refused to register it.

As for virt-manager, it looked so promising in regular kernel mode.  In fact that does work properly, for kvm and qemu.  Once entered a xen environment, the virt-manager loses its way.  It couldn't connect to anything at first.  I finally got it to connect to xen, but it still could not connect to qemu, which it should do.  Reason, more perplexing info.  /var/run/libvirt/...sock  No such file or directory.  xen appears to be the culprit.
It works properly booting a regular kernel.  i.e. The sockets are made.  I wondered if it was the kernel, but the kernel has the same config as the one that boots lenny where this doesn't happen.

There are about four separate deficits here.  If anyone can offer resolutions, well and good, but I don't think so.  This is a level of integration of technical aspects of a number of different packages that only developers could unravel.

The winner is Suse.  Its integrated packages have a few misfires, but you can create and run and manage vms.  Ubuntu, why oh why deliver such a list of deficits.  
Did jaunty get it right?  Do I have to check the older versions to see if they actually worked to get a working version?

I'm going to do a rerun of this just to check, and hopefully I can post some better news.
Can someone prove me wrong?

Probably not.  After reinstalling all xen related software, it still does the same.  There is a mode I don't understand at all called test:///
It's a manufactured hypervisor choice.  On attempting to create a new vm using it, it falls short yet again.  Just like in lenny, the guest is unconfigured for the virt-manager console. Still no bridge for a guest.  **Basically unusable**.

You can only use virt manager in a regular kernel for qemu and kvm.  xen just **doesn't work**

---

