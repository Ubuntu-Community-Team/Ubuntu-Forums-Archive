---
title: "Running Windows Inside Kubuntu from Existing Partition?"
date: 2011-10-18
forum: Desktop Environments
---

### Post by LiamMaru on 2011-10-18
Hey Guys,

I've found older posts on this topic, but wanted to know if there have been any newer developments.

I've got a machine which has a pre-existing Windows 7 installation, and I'd like to put Kubuntu on it for doing things only Linux will let me do. I'd like to keep my Windows partition, however access it from my Kubuntu partition, similar to how I would with VMWare, with the host/guest type setup except that the 'guest' operating system is installed and accessed from another partition. Is this possible and, if so, how would I go about achieving this? I'd only want to access Windows 7 from Kubuntu, not vice versa.

Thanks,

Liam

---

### Post by Aide9aic on 2011-10-30
You could use VMware's free [vCenter Converter]("http://www.vmware.com/products/converter/") to convert your Windows machine to a virtual machine while it's running. Then install Kubuntu, install [VMware Player]("http://www.vmware.com/products/player/"), and run your newly-converted Windows VM. I followed exactly this procedure to migrate from Windows 7 to Kubuntu, and it worked without a hitch.

---

### Post by Mark Phelps on 2011-10-30
If you keep BOTH the installed Win7 and run it in a VM as well, every time you launch Win7, it will have to be reactivated -- because the hardware profile looks different from inside the VM.  Even with a retail version, after a few reactivations, it will refuse to reactivate again.  Doing this will basically trash your Win7 setup.

---

### Post by Aide9aic on 2011-10-30
True, I neglected to mention that. Thanks for adding. I figured the OP's goal was to replace Windows but keep existing data intact. The other approach, of course, is to set up [dual-boot](https://help.ubuntu.com/community/WindowsDualBoot). After Kubuntu boots, you can mount the Windows partition and access the data there.

---

### Post by Mark Phelps on 2011-10-31
I only mention it, because this little-known problem is almost never mentioned when folks want to re-use their existing Win7 install but in a Virtualized environment.

It's pretty disappointing to suddenly find your bought-and-paid-for install of Win7 refusing to work because you unknowingly exceeded some UNPUBLISHED number of reactivations!

---

