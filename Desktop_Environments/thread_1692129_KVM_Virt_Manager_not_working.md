---
title: "KVM Virt Manager not working"
date: 2011-02-21
forum: Desktop Environments
---

### Post by MechaMechanism on 2011-02-21
EDIT:  Networking works under root.  I wanted to run under my account without elevated privileges, but that don't work.  So for now I just run KVM with gksu.  Looks like my issue is account permissions issue.


I use Ubuntu 10.04.2.  I installed virt manager.  I can't create virtual machine.

I am running in usermode.  I do not want nor do I need to run as root.  I just want to create virtual machine and use usermode networking.  I don't need bridge.

Error message.
Unable to complete install: 'internal error unable to start guest: char device redirected to /dev/pts/2
qemu: could not open disk image /var/lib/libvirt/images/ubuntu.img: No such file or directory

Error message 2.
Unable to complete install '<class 'libvirt.libvirtError'> internal error unable to start guest: char device redirected to /dev/pts/2
qemu: could not open disk image /var/lib/libvirt/images/ubuntu.img: No such file or directory

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 1436, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 660, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 758, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1097, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error unable to start guest: char device redirected to /dev/pts/2
qemu: could not open disk image /var/lib/libvirt/images/ubuntu.img: No such file or directory

---

