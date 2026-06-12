---
title: "qemu 8.0.8 and it's samba mechanism"
date: 2006-01-12
forum: General Help
---

### Post by dentament on 2006-01-12
Hi.
I installed from sources qemu 8.0.8 with kqemu (it's accelerator).
It works perfectly but for one thing: when launching it with the -smb switch, like this...

qemu -boot c -hda w2k.img -smb /home/xxx/Desktop

...which should give access, from the emulated w2k, to /home/xxx/Desktop folder on the linux filesystem, this doesn't work.

It seems that the thing should work this way: every time I try to access \\smbserver\qemu from the emulated w2k (yes i got "10.0.2.4 smbserver" in c:\winnt\system32\drivers\etc\hosts), qemu first creates a temporary config dir for the samba process it's about to launch (under /tmp - like /tmp/qemu-smb.9002/ ) where it puts an smb.conf which it creates, and then launches smbd "against" this config file --- the problem is that the "smbd" process it launches this way, soon dies: by doing a "ps -A" I can see a "smbd [defunct]" for every time I tried to access \\smbserver\qemu from the emulated w2k. Looking at the log file each smbd processes launched by qemu creates in the temporary dir before dying (for example /tmp/qemu-smb.9002/log.smbd), I can always read stuff like this:

------
[2006/01/12 11:20:10, 1] smbd/files.c:file_init(198)
  file_init: Information only: requested 10000 open files, 1004 are available.
[2006/01/12 11:20:10, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb
[2006/01/12 11:20:10, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb
[2006/01/12 11:20:10, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb
[2006/01/12 11:20:10, 0] passdb/machine_sid.c:pdb_generate_sam_sid(176)
  pdb_generate_sam_sid: Failed to store generated machine SID.
[2006/01/12 11:20:10, 0] lib/util.c:smb_panic2(1495)
  PANIC: Could not generate a machine SID
  
[2006/01/12 11:20:10, 0] lib/util.c:smb_panic2(1503)
  BACKTRACE: 7 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0x79) [0x81d3463]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81d3660]
   #2 /usr/sbin/smbd(get_global_sam_sid+0x287) [0x8192ba7]
   #3 /usr/sbin/smbd(init_guest_info+0x5a) [0x82100a0]
   #4 /usr/sbin/smbd(main+0x2a2) [0x8246335]
   #5 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d37ea2]
   #6 /usr/sbin/smbd [0x8079a11]
[2006/01/12 11:20:10, 1] smbd/files.c:file_init(198)
  file_init: Information only: requested 10000 open files, 1004 are available.
[2006/01/12 11:20:10, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb
[2006/01/12 11:20:10, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb
[2006/01/12 11:20:10, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb
[2006/01/12 11:20:10, 0] passdb/machine_sid.c:pdb_generate_sam_sid(176)
  pdb_generate_sam_sid: Failed to store generated machine SID.
[2006/01/12 11:20:10, 0] lib/util.c:smb_panic2(1495)
  PANIC: Could not generate a machine SID
  
[2006/01/12 11:20:10, 0] lib/util.c:smb_panic2(1503)
  BACKTRACE: 7 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0x79) [0x81d3463]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81d3660]
   #2 /usr/sbin/smbd(get_global_sam_sid+0x287) [0x8192ba7]
   #3 /usr/sbin/smbd(init_guest_info+0x5a) [0x82100a0]
   #4 /usr/sbin/smbd(main+0x2a2) [0x8246335]
   #5 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7cbdea2]
   #6 /usr/sbin/smbd [0x8079a11]
------

...and don't know what to do.
It seems to be a samba problem, but samba here works perfectly when launched from it's init script.

Thanks for any suggestion
Bye

---

### Post by akaihola on 2006-09-16
Exactly the same problem here with qemu from current cvs on Dapper.

---

### Post by akaihola on 2006-09-16
One solution seems to be to run qemu as root (with sudo).

---

