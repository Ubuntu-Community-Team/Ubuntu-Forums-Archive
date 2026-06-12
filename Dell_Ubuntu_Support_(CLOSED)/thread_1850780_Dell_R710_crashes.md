---
title: "Dell R710 crashes"
date: 2011-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adrianmarsh-ubi on 2011-09-27
Hi,

We've a Dell R710 running Ubuntu 10.04.3 LTS, which at least once a week is spontaneously crashing. The crashes sometimes leave no logging trace at all, the machine just locks up, and other times we'll see logs that make me suspicious of the smbd daemon.

The machine is basically used for compilation, and the files are access over SMB shares.

The sysadmins of the machine tell me its patched up-to-date, and that this must be a hardware issue.

I've a ticket open with Dell. We've updated USC and all of the firmwares (expect the network cards) to the latest Dell recommended firmwares.  We've run the Dell Diags several times. The iDRAC doesn't register any h/w faults at all.  We did manage to get a 3rd party OS/tool called memtest86 to crash, complaining about an interrupt on CPU0, but, we've never used that tool before and of course Dells memory testing tool ran for hours with no issue.

My next step, is to start running CPU and I/O stats to see what the systems really doing when the crash next occours, and then see if I can find a pattern.

but I'm not familiar with Ubuntu, my background being Solaris/Redhat really.  I'm not sure which logging tools Ubuntu has for doing this, either automatically or manually.

Dells last recommendation was that we tweak a BIOS setting that controlled CPU power levels (C-STATES to disabled), but yesterday the machine again crashed.

Does Ubuntu store any crash logs?

below is the messages log the sysadmins sent me from its last crash

> 
Sep 26 15:04:23 my-serv11 nagios3: SERVICE ALERT: localhost;Current Load;WARNING;SOFT;1;WARNING - load average: 3.45, 4.07, 2.88
Sep 26 15:05:01 my-serv11 nmbd[1429]: [2011/09/26 15:05:01,  0] nmbd/nmbd_namequery.c:108(query_name_response)
Sep 26 15:05:01 my-serv11 nmbd[1429]:   query_name_response: Multiple (2) responses received for
a query on subnet 192.168.50.111 for name mycompany<1d>.
Sep 26 15:05:01 my-serv11 nmbd[1429]:   This response was from IP 192.168.50.28, reporting an IP
address of 192.168.50.60.
Sep 26 15:06:37 my-serv11 kernel: [457849.957425] BUG: soft lockup - CPU#5 stuck for 61s! [smbd:1172]
Sep 26 15:06:37 my-serv11 kernel: [457849.957733] Modules linked in: cramfs nls_cp437 cifs aufs mpt2sas scsi_transport_sas mptctl mptbase dell_rbu nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc joydev usbhid hid coretemp ipmi_devintf fbcon tileblit font bitblit softcursor vga16fb vgastate dell_wmi dcdbas psmouse serio_raw ipmi_si power_meter bnx2 ipmi_msghandler lp parport raid10 raid456 async_raid6_recov async_pq ses enclosure raid6_pq async_xor xor async_memcpy async_tx raid1 megaraid_sas raid0 multipath linear
Sep 26 15:06:37 my-serv11 kernel: [457849.957764]
Sep 26 15:06:37 my-serv11 kernel: [457849.957766] Pid: 1172, comm: smbd Not tainted (2.6.32-32-generic-pae #62-Ubuntu) PowerEdge R710
Sep 26 15:06:37 my-serv11 kernel: [457849.957769] EIP: 0060:[<c018542a>] EFLAGS: 00000202 CPU: 5
Sep 26 15:06:37 my-serv11 kernel: [457849.957773] EIP is at smp_call_function_many+0x18a/0x200
Sep 26 15:06:37 my-serv11 kernel: [457849.957775] EAX: 00000286 EBX: 00000007 ECX: 00000008 EDX:
00000008
Sep 26 15:06:37 my-serv11 kernel: [457849.957777] ESI: c9944b18 EDI: c9944b30 EBP: f420be00 ESP:
f420bde0
Sep 26 15:06:37 my-serv11 kernel: [457849.957779]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Sep 26 15:06:37 my-serv11 kernel: [457849.957780] CR0: 8005003b CR2: b70dc000 CR3: 34e02000 CR4:
000006f0
Sep 26 15:06:37 my-serv11 kernel: [457849.957782] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3:
00000000
Sep 26 15:06:37 my-serv11 kernel: [457849.957784] DR6: ffff0ff0 DR7: 00000400
Sep 26 15:06:37 my-serv11 kernel: [457849.957785] Call Trace:
Sep 26 15:06:37 my-serv11 kernel: [457849.957790]  [<c01da4f0>] ? drain_local_pages+0x0/0x20
Sep 26 15:06:37 my-serv11 kernel: [457849.957792]  [<c01da4f0>] ? drain_local_pages+0x0/0x20
Sep 26 15:06:37 my-serv11 kernel: [457849.957795]  [<c01854c4>] smp_call_function+0x24/0x30
Sep 26 15:06:37 my-serv11 kernel: [457849.957800]  [<c015b5af>] on_each_cpu+0x1f/0x50
Sep 26 15:06:37 my-serv11 kernel: [457849.957802]  [<c01d9709>] drain_all_pages+0x19/0x20
Sep 26 15:06:37 my-serv11 kernel: [457849.957805]  [<c01d9a25>] __alloc_pages_slowpath+0x255/0x4a0
Sep 26 15:06:37 my-serv11 kernel: [457849.957808]  [<c01d9daa>] __alloc_pages_nodemask+0x13a/0x170
Sep 26 15:06:37 my-serv11 kernel: [457849.957811]  [<c01d9dfc>] __get_free_pages+0x1c/0x30
Sep 26 15:06:37 my-serv11 kernel: [457849.957813]  [<c01524fd>] dup_task_struct+0x3d/0x120
Sep 26 15:06:37 my-serv11 kernel: [457849.957815]  [<c0153448>] copy_process+0x88/0xc20
Sep 26 15:06:37 my-serv11 kernel: [457849.957818]  [<c01707d0>] ? autoremove_wake_function+0x0/0x50
Sep 26 15:06:37 my-serv11 kernel: [457849.957821]  [<c0154063>] do_fork+0x83/0x3a0
Sep 26 15:06:37 my-serv11 kernel: [457849.957825]  [<c04dcbb4>] ? sys_socketcall+0xb4/0x280
Sep 26 15:06:37 my-serv11 kernel: [457849.957830]  [<c0107e49>] sys_clone+0x39/0x50
Sep 26 15:06:37

  

---

