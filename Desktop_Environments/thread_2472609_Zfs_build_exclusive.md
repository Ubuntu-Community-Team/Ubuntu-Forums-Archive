---
title: "Zfs build exclusive"
date: 2022-03-06
forum: Desktop Environments
---

### Post by alexloz on 2022-03-06
Hi, when trying to install the zfs-dkms package, I get an error that the module can't be built. This doesn't stop Ubuntu from thinking that the package is installed, but ```
zfs --version
``` returns no module found. What am I missing?

```

The following NEW packages will be installed:
  zfs-dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,896 kB of archives.
After this operation, 14.5 MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package zfs-dkms.
(Reading database ... 198015 files and directories currently installed.)
Preparing to unpack .../zfs-dkms_0.8.3-1ubuntu12.13_all.deb ...
Unpacking zfs-dkms (0.8.3-1ubuntu12.13) ...
Setting up zfs-dkms (0.8.3-1ubuntu12.13) ...
Loading new zfs-0.8.3 DKMS files...
Building for 5.13.0-30-generic
Building initial module for 5.13.0-30-generic
Error!  The /var/lib/dkms/zfs/0.8.3/5.13.0-30-generic/x86_64/dkms.conf for module zfs includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Skipped.
Processing triggers for initramfs-tools (0.136ubuntu6.7) ...

```

---

### Post by deadflowr on 2022-03-06
zfs-dkms in provided by the generic kernels already.
(It's baked into the kernel package.)

What you need is not the modules but the zfsutils-linux package,
or whatever it's called.

---

### Post by alexloz on 2022-03-07
I already have that installed, that's how I could run zfs --version, which I believe is a part of that package. That installed fine.

---

### Post by alexloz on 2022-03-07
Well, upon further investigation, it's simply not loading sometimes:

```

# journalctl -u zfs-load-module.service
-- Logs begin at Sat 2022-02-26 17:45:47 EST, end at Mon 2022-03-07 18:17:01 EST. --
Feb 28 18:04:40 myhost systemd[1]: Starting Install ZFS kernel module...
Feb 28 18:04:40 myhost systemd[1]: Finished Install ZFS kernel module.
-- Reboot --
Feb 28 23:36:32 myhost systemd[1]: Starting Install ZFS kernel module...
Feb 28 23:36:33 myhost systemd[1]: Finished Install ZFS kernel module.
-- Reboot --
Mar 01 23:15:29 myhost systemd[1]: Starting Install ZFS kernel module...
Mar 01 23:15:30 myhost systemd[1]: Finished Install ZFS kernel module.
-- Reboot --
Mar 01 23:43:33 myhost systemd[1]: Dependency failed for Install ZFS kernel module.
Mar 01 23:43:33 myhost systemd[1]: zfs-load-module.service: Job zfs-load-module.service/start failed with result 'dependency'.
-- Reboot --
Mar 02 07:53:22 myhost systemd[1]: Dependency failed for Install ZFS kernel module.
Mar 02 07:53:22 myhost systemd[1]: zfs-load-module.service: Job zfs-load-module.service/start failed with result 'dependency'.
-- Reboot --
Mar 02 08:06:32 myhost systemd[1]: Dependency failed for Install ZFS kernel module.
Mar 02 08:06:32 myhost systemd[1]: zfs-load-module.service: Job zfs-load-module.service/start failed with result 'dependency'.
-- Reboot --
Mar 02 13:03:21 myhost systemd[1]: Starting Install ZFS kernel module...
Mar 02 13:03:21 myhost systemd[1]: Finished Install ZFS kernel module.
-- Reboot --
Mar 02 13:31:53 myhost systemd[1]: Dependency failed for Install ZFS kernel module.
Mar 02 13:31:53 myhost systemd[1]: zfs-load-module.service: Job zfs-load-module.service/start failed with result 'dependency'.
-- Reboot --
Mar 02 14:24:06 myhost systemd[1]: Dependency failed for Install ZFS kernel module.
Mar 02 14:24:06 myhost systemd[1]: zfs-load-module.service: Job zfs-load-module.service/start failed with result 'dependency'.
-- Reboot --
Mar 06 00:12:48 myhost systemd[1]: Dependency failed for Install ZFS kernel module.
Mar 06 00:12:48 myhost systemd[1]: zfs-load-module.service: Job zfs-load-module.service/start failed with result 'dependency'.
-- Reboot --
Mar 06 20:04:56 myhost systemd[1]: Starting Install ZFS kernel module...
Mar 06 20:04:57 myhost systemd[1]: Finished Install ZFS kernel module.

```

---

### Post by alexloz on 2022-03-07
More info, it's being caused because of:

```

Mar 06 00:10:48 myhost systemd[1]: Starting udev Wait for Complete Device Initialization...
Mar 06 00:11:32 myhost udevadm[977]: systemd-udev-settle.service is deprecated.
Mar 06 00:12:48 myhost systemd[1]: systemd-udev-settle.service: Main process exited, code=exited, status=1/FAILURE
Mar 06 00:12:48 myhost systemd[1]: systemd-udev-settle.service: Failed with result 'exit-code'.
Mar 06 00:12:48 myhost systemd[1]: Failed to start udev Wait for Complete Device Initialization.

```

which causes...

```

[COLOR=#1D1C1D][FONT=Slack-Lato]Mar 01 23:43:33 [/FONT][/COLOR]myhost [COLOR=#1D1C1D][FONT=Slack-Lato]systemd[1]: Dependency failed for Install ZFS kernel module.[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]Mar 01 23:43:33 [/FONT][/COLOR]myhost [COLOR=#1D1C1D][FONT=Slack-Lato]systemd[1]: zfs-load-module.service: Job zfs-load-module.service/start failed with result 'dependency'.
[/FONT][/COLOR]
```

---

