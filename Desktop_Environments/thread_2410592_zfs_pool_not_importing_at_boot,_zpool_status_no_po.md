---
title: "zfs pool not importing at boot, zpool status no pools available, mirror died"
date: 2019-01-17
forum: Desktop Environments
---

### Post by rhalkes2 on 2019-01-17
First post here on ubuntu forums, 

During boot I'm getting the message:
----
SPL: The /etc/hostid file is not found
SPL: using hostid 0x00000000
random: nonblocking pool is initialized
WARNING: can't open objset 85, error 5
Command: zpool import -N odin
Message: cannot import 'odin': one or more devices is currently unavailable
Error: 1

Manually import the root pool at the command prompt and then exit. 
Hint: Try zpool import -f -R / -N odin

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
----

When I try running "zpool import -f -R / -N odin"

I get the message "Warning: Can't open objset 85, error 5
cannot import 'odin': one or more devices is currently unavailable"

 
Running :zpool status: returns "no pool available"

running "zpool import: I see 

(initramfs) zpool import
pool: odin
id: 1052369....................
state: DEGRADED
status: One or more devices contains corrupted data.
action: The pool can be imported despite missing or damaged devices. The
fault tolerance of the pool may be compromised if imported.
see: [http://zfsonlinux.org/msg/ZFS-8000-4J](http://zfsonlinux.org/msg/ZFS-8000-4J)
config: 


odin                                                                                                                    degraded
       mirror-0                                                                                                       degraded
            ata-Samsung_SSD_850_EVO_500GB__S2RAN..................part2                 ONLINE
            789988745074390257                                                                              Faulted Corrupted data

...




Can I just import the drive and ignore the missing mirror? I just need to get the files off of the drive so If I can't boot I just need to mount my home folder.

---

