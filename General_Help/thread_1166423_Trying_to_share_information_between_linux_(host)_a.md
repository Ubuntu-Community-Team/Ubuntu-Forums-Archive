---
title: "Trying to share information between linux (host) and VirtualBox. Windows (guest)"
date: 2009-05-21
forum: General Help
---

### Post by kd0afk on 2009-05-21
The documentation makes no sense to me. Might as well have been printed in wingdings. Does someone have some advice in layman's terms?

---

### Post by albinootje on 2009-05-21
> **kd0afk said:**
> The documentation makes no sense to me. Might as well have been printed in wingdings. Does someone have some advice in layman's terms?

Are you using a recent version (2.1 or 2.2) of VirtualBox ?
Then you can choose "bridged adapter" in the VirtualBox network settings of the guest VM which makes things easier than NAT imho.

After that install the meta-package "ssh" on your Ubuntu host, and then install WinSCP ([http://winscp.sf.net](http://winscp.sf.net)) in your guest VM, and start winscp to log in to your host to share files.

---

### Post by Greenwidth on 2009-05-21
Did you install Guest Additions?
With the virtual machine running Devices > Install Guest Additions.
After installing, shut it down (the virtual machine)

Define the folders you want to share in:
Settings > Shared Folders (add on the right)

Boot the virtual machine and browse in Explorer to:
Network Places > Add a networkplace > VirtualBox Shared Folders.

---

