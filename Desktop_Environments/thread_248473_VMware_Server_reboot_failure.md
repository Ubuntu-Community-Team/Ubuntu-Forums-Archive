---
title: "VMware Server reboot failure"
date: 2006-09-01
forum: Desktop Environments
---

### Post by heffo_j on 2006-09-01
I've loaded and installed VMserver. It is absolutely brilliant; the way of the future. However, after a reboot, I have to reconfigure the install to get it running again. 

Are there other Dapper uses facing the same problem. Is there a fix?

This is the root log file after I have it running:

Sep 01 17:39:02: vmui| Log for VMware Server pid=7019 version=1.0.1 build=build-29996 option=Release
Sep 01 17:39:02: vmui| Using log file /tmp/vmware-root/ui-7019.log
Sep 01 17:39:02: vmui| HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
Sep 01 17:39:02: vmui| HAL05LoadGlibLibrary: Could not dlopen libdbus-glib-1.so.1.
Sep 01 17:39:02: vmui| HAL05Init: HAL05 Initialized successfully.
Sep 01 17:39:03: vmui| HOSTINFO: Seeing Intel CPU, numCoresPerCPU 1 numThreadsPerCore 1.
Sep 01 17:39:03: vmui| HOSTINFO: This machine has 1 physical CPUS, 1 total cores, and 1 logical CPUs.
Sep 01 17:39:03: vmui| System libcrypto.so.0.9.7 library is older than our library (90707F < 90709F)
Sep 01 17:39:04: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Stop and Stop
Sep 01 17:39:04: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Forward and _Forward
Sep 01 17:39:04: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Information and Information
Sep 01 17:39:15: vmui| Caught signal 1 -- pid 7019 (eip 0xffffe410)

Perhaps there is someone technically gifted who can make something of this and direct me to a solution.

Thank you in advance.

John

---

### Post by heffo_j on 2006-09-01
Its all okay now. I should have completely uninstalled all the vm-ware  kernel modules which I had previously loaded when I first tried vm-player. It now boots correctly. 

I have installed the latest version of vmware-server (free). I can run xp with nor problems from within Dapper. I'm happy.

Regards
John

---

### Post by hraposo on 2006-09-01
How you install vmware-server? When I try install give me the message:> Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.

---

### Post by hraposo on 2006-09-01
I already installed the vmware! I just had to copy the vmware to tmp directory and execute the installer.

---

