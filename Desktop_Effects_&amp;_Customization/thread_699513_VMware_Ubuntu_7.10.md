---
title: "VMware Ubuntu 7.10"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by gunbait101 on 2008-02-17
Alright, my problem is I have VMware installed on my laptop and I can run Ubuntu just fine.

I have done the following...

1.) Compiz-Fusion
2.) VMware tools
3.) and a bunch of other things.

What is wrong is that my desktop enhancements just won't work, it says "desktop enhancements can't be used" or something to that affect.

Any suggestions?

---

### Post by e020613 on 2008-02-17
I have done the following...
...
3.) and a bunch of other things.
...

Well, I am pretty much sure no one in this forum has a glimpse of what this could mean -- especially if you yourself can't remember what you did. Have a second thougt, revert your settings "mentionend" under 3.), and post again.

---

### Post by gunbait101 on 2008-02-17
Downloaded Xserver my friend told me to do, got restricted drivers, disabled restricted drivers, configured it directly through vmware-tools &...

---

### Post by VMan on 2008-02-18
I'm not entirely clear on what you are asking:
1.  Are you trying to enable advanced desktop effects in the virtual machine
          or
2.)  Are you trying to enable them in the host?

If #1, you can't use them in the virtual machine currently.  The virtual machine's video card doesn't support them yet.  I'm hoping that it will eventually support them.  I use several virtual machines and would love to see this.

  Sorry I wasn't much help.

---

### Post by FuturePilot on 2008-02-18
If you're trying to use Compiz in the VM, it won't work. VMs can't handle 3D stuff.

---

