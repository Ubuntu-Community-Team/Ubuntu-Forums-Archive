---
title: "vmware workstation"
date: 2007-05-08
forum: Desktop Environments
---

### Post by n_hendrick on 2007-05-08
I was wondering if there is a way to get hardware video acceleration on vmware workstation 6. I am running a nvidia geforce 7600 and a 2.6.20-15i386 kernel. Is it as simple as installing the nvidia drivers inside the virtual machine?

---

### Post by ohgod on 2007-05-08
I'm not sure that's possible.  I've read some forums on this subject on vmware's site, and the general consensus seems to be that if you need hardware acceleration for graphics, vmware isn't the right solution.   But I'd search there to get a better idea.

[http://www.vmware.com/community/index.jspa]("http://www.vmware.com/community/index.jspa")

---

### Post by jaffa_nz on 2007-05-09
That's correct.  Installation of the VMware Tools is required for anysort of useage/performance, and as part the video drivers are loaded.

---

### Post by n_hendrick on 2007-05-12
Well supposedly in 6.0 VMware is suppose to support directx.....I guess I'll just have to buy it.....

---

### Post by veloce on 2007-05-13
> **n_hendrick said:**
> Well supposedly in 6.0 VMware is suppose to support directx.....I guess I'll just have to buy it.....

I understand VMWare Workstation has **experimental** 3D support.  I use the free vmware server so have no experience with that.  I would want to be very sure it worked on your hardware before shelling out $$$

---

### Post by Jhongy on 2007-05-14
VMWare WorkStation 6 release candidate  is freely downloadable from the VMWare site... (do a Google search for VMWare Workstation Beta).

I'm using it, but haven't seen any mentions of 3D acceleration... if you find anything, let me know :-) . I installed the VMWare tools, but Windows just shows a VMWare SVGA driver. It's smoother as butter, but no 3D.

P.S. It fails to install unless you comment out a line specific to older kernels in the installer script... it should be relatively easy to find, but if you can't figure it out, post & I can try to dig up what I did. Once it's installed, it's rock solid.

---

### Post by veloce on 2007-05-14
> **Jhongy said:**
> VMWare WorkStation 6 release candidate  is freely downloadable from the VMWare site... (do a Google search for VMWare Workstation Beta).

I'm using it, but haven't seen any mentions of 3D acceleration... if you find anything, let me know :-) . I installed the VMWare tools, but Windows just shows a VMWare SVGA driver. It's smoother as butter, but no 3D.

P.S. It fails to install unless you comment out a line specific to older kernels in the installer script... it should be relatively easy to find, but if you can't figure it out, post & I can try to dig up what I did. Once it's installed, it's rock solid.

This thread: [http://ubuntuforums.org/showthread.php?t=84344](http://ubuntuforums.org/showthread.php?t=84344)

Indicates how to get 3d working on workstation 5 - implication is that it will also work on 6, maybe player but not server (though someone said they got the Sims 2 working on server????)

---

