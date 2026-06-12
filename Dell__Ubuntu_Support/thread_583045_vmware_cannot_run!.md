---
title: "vmware cannot run!"
date: 2007-10-20
forum: Dell  Ubuntu Support
---

### Post by JangMunho on 2007-10-20
I compiled the new kernel 2.6.23.1 on my 1420 which installed ubuntu 7.04. But vmware 6 workstation won't work under the new kernel, even though I tried to install the new version of vmware (6.0.1 55017).

When i type "sudo vmware" in the terminal window, it returned such error message:
```
zhanggm@ubuntu:~$ sudo vmware
Password:
[COLOR="Red"]/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/gtk-2.0/modules/libatk-bridge.so: undefined symbol: atk_misc_get_instance[/COLOR]
zhanggm@ubuntu:~$ 

```

Anybody know how to deal with it?

---

### Post by kikazaru on 2007-11-15
No, but I'm getting the same problem. I read a post on a Fedora forum that said that if you disable accessibility then the problem goes away, but I have no idea what that means, nor whether it is appropriate under Ubuntu. 

I had vmware running before I upgraded from Feisty to Gutsy.

---

### Post by RobertGloverJr on 2007-11-16
On a desktop computer (not a Dell) I was able to install Ubuntu 7.10 and then install Vmware Workstation 6 on top of it.  It worked fine.  I then installed WindowXP as a guest OS.  But that was a clean install starting with nothing.
   The Vmware Workstation 6.x User Guide says that Vmware supports 7.04 but it does not say it supports 7.10.  
   On my Dell Inspiron 1420n (which came with 7.04 factory installed) I installed Vmware Workstation 6.x and then installed the OLPC (One Laptop Per Child) as a guest OS.  That was really fun.  You should try it when you are back up. 
    What I've been meaning to do is to trying installing 7.10 as a guest OS under vmware that itself is running under 7.04.    Has anybody tried that yet?

---

### Post by inaneframe on 2007-11-16
I recommend that you try Innotek's Virtualbox, the open source edition is in the repositories of Ubuntu.

As easy to install as any other Ubuntu package and a smooth run all together.  It also allows for a VERY easy single click download and install of Virtualbox's "Guest Additions" image that adds those special drivers that allow better integration with the host OS for each VM, much like VMWare.

---

### Post by veloce on 2007-11-16
I would assume that, like vmware server, vmware workstation would need to have new modules compiled for each change in kernel.

With vmware server this is accomplished by running "vmware-config.pl" after each kernel change.

vmware server works fine under Gutsy (once the modules are compiled)

---

