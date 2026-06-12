---
title: "Can I boot into a virtual machine?"
date: 2009-02-21
forum: General Help
---

### Post by codescribler on 2009-02-21
Hi All,

I would like to try and boot my machine in Linux and load a windows xp virtual machine. The issue is I don't need to boot into Linux I just want to be able to boot the absolute minimum Linux need to run a virtual machine.

Why do I want to do this?
It makes my windows xp machine mega easy to backup. I can also have a bunch of different XP machines for different tasks. Clearly, there will be times I want to boot into Linux but maybe that will be a virtual machine as well.

Any tips out there?

Danny
PS. I know windows well and I do have a Linux laptop but dont know it very well (still stuck in the GUI and am completely lost in VI).

---

### Post by yeleek on 2009-02-21
Don't think you'll get what you want with ubuntu.  Vmware wks/srv and virtual box will require access to all the various system resources and filesystems to be able to give you your virtual machine - including access to video driver, usb/cd, etc etc.

If you want a streamlined version of linux to host vm's then look here:
[http://www.vmware.com/products/esxi/](http://www.vmware.com/products/esxi/)
[http://www.vmware.com/products/vi/esx/](http://www.vmware.com/products/vi/esx/)

But this is enterprise level tech - not something a home user would have necessarily.

i.e
"Bare-metal architecture.  VMware ESXi inserts a robust virtualization layer directly on the server hardware for near-native virtual machine performance, reliability and scalability."

---

