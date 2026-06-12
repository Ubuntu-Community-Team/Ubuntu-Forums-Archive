---
title: "[HELP] User Mode Linux won't run with Copy on Write :( :("
date: 2009-04-17
forum: General Help
---

### Post by topimiring on 2009-04-17
Hello,
Firstly , forgive me If I post this in the wrong sub-forum (because I don't find any suitable sub-forum to post this topic on this forum). So here is my probz.
I'm running Ubuntu 8.04 2.6.24-19-generic. And I am currently experimenting with user mode linux to run debian OS (2.6.22-rc5) inside the UML. I firstly tried to run it without COW :
linux ubd0=rootfs.ext3 umid=testajahxxxxxx

and it worked fine. 

And then i tried to run it with COW :
linux ubd0=testajah.cow,rootfs.ext3 umid=testajahxxxxxx 

And it returned with :

```
Core dump limits :
	soft - 0
	hard - NONE
Checking that ptrace can change system call numbers...OK
Checking syscall emulation patch for ptrace...OK
Checking advanced syscall emulation patch for ptrace...OK
Checking for tmpfs mount on /dev/shm...OK
Checking PROT_EXEC mmap in /dev/shm/...OK
Checking for the skas3 patch in the host:
  - /proc/mm...not found: No such file or directory
  - PTRACE_FAULTINFO...not found
  - PTRACE_LDT...not found
UML running in SKAS0 mode
[42949372.960000] Linux version 2.6.22-rc5 (root@vernadsky) (gcc version 4.1.3 20070629 (prerelease) (Ubuntu 4.1.2-13ubuntu2)) #2 Mon Jul 2 10:14:22 GMT 2007
[42949372.960000] Built 1 zonelists.  Total pages: 8128
[42949372.960000] Kernel command line: ubd0=testajah.cow,rootfs.ext3 root=98:0
[42949372.960000] PID hash table entries: 128 (order: 7, 512 bytes)
[42949372.960000] Dentry cache hash table entries: 4096 (order: 2, 16384 bytes)
[42949372.960000] Inode-cache hash table entries: 2048 (order: 1, 8192 bytes)
[42949372.960000] Memory: 29316k available
[42949373.250000] Mount-cache hash table entries: 512
[42949373.250000] Checking for host processor cmov support...Yes
[42949373.250000] Checking for host processor xmm support...No
[42949373.250000] Checking that host ptys support output SIGIO...Yes
[42949373.250000] Checking that host ptys support SIGIO on close...No, enabling workaround
[42949373.250000] Using 2.6 host AIO
[42949373.250000] NET: Registered protocol family 16
[42949373.300000] NET: Registered protocol family 2
[42949373.410000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[42949373.410000] TCP established hash table entries: 1024 (order: 1, 8192 bytes)
[42949373.410000] TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
[42949373.410000] TCP: Hash tables configured (established 1024 bind 1024)
[42949373.410000] TCP reno registered
[42949373.440000] Checking host MADV_REMOVE support...OK
[42949373.440000] mconsole (version 2) initialized on /root/.uml/testajahxxxxxx/mconsole
[42949373.440000] Mapper v0.1
[42949373.440000] mmapper_init - find_iomem failed
[42949373.440000] UML Watchdog Timer
[42949373.440000] Host TLS support detected
[42949373.440000] Detected host type: i386
[42949373.440000] VFS: Disk quotas dquot_6.5.1
[42949373.440000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949373.440000] JFS: nTxBlock = 229, nTxLock = 1832
[42949373.440000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[42949373.440000] SGI XFS Quota Management subsystem
[42949373.440000] io scheduler noop registered
[42949373.440000] io scheduler anticipatory registered (default)
[42949373.440000] io scheduler deadline registered
[42949373.440000] io scheduler cfq registered
[42949373.710000] SoftDog: cannot register miscdev on minor=130 (err=-16)
[42949373.720000] TCP cubic registered
[42949373.720000] NET: Registered protocol family 1
[42949373.720000] NET: Registered protocol family 17
[42949373.720000] Initialized stdio console driver
[42949373.720000] Console initialized on /dev/tty0
[42949373.720000] Initializing software serial port version 1
[42949373.800000] Creating "testajah.cow" as COW file for "rootfs.ext3"
[42949373.800000] F_SETLK failed, file already locked by pid 13966
[42949373.800000] Failed to lock 'rootfs.ext3', err = 11
[42949373.800000] ubda: Can't open "testajah.cow": errno = 11
[42949373.800000] F_SETLK failed, file already locked by pid 13966
[42949373.800000] Failed to lock '/root/rootfs.ext3', err = 11
[42949373.800000] ubda: Can't open "testajah.cow": errno = 11
[42949373.800000] VFS: Cannot open root device "98:0" or unknown-block(98,0)
[42949373.800000] Please append a correct "root=" boot option; here are the available partitions:
[42949373.800000] 6200     819200 ubda driver: uml-blkdev
[42949373.800000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(98,0)
[42949373.800000] 
[42949373.800000] EIP: 0073:[<b7f25410>] CPU: 0 Not tainted ESP: 007b:b7dcdfb4 EFLAGS: 00000246
[42949373.800000]     Not tainted
[42949373.800000] EAX: 00000000 EBX: 00003a8d ECX: 00000013 EDX: 00003a8d
[42949373.800000] ESI: 00003a89 EDI: 00000011 EBP: b7dcdfd8 DS: 007b ES: 007b
[42949373.800000] 08323e64:  [<0806ce8c>] show_regs+0xb4/0xb9
[42949373.800000] 08323e90:  [<0805b038>] panic_exit+0x25/0x3f
[42949373.800000] 08323ea4:  [<0807c418>] notifier_call_chain+0x21/0x46
[42949373.800000] 08323ec4:  [<0807c4b3>] __atomic_notifier_call_chain+0x17/0x19
[42949373.800000] 08323ee0:  [<0807c4ca>] atomic_notifier_call_chain+0x15/0x17
[42949373.800000] 08323efc:  [<08071532>] panic+0x52/0xd8
[42949373.800000] 08323f1c:  [<08049b4f>] mount_block_root+0x100/0x116
[42949373.800000] 08323f70:  [<08049bb1>] mount_root+0x4c/0x54
[42949373.800000] 08323f94:  [<08049c8f>] prepare_namespace+0xd6/0x102
[42949373.800000] 08323fa4:  [<08049874>] kernel_init+0x79/0x85
[42949373.800000] 08323fb4:  [<08067315>] run_kernel_thread+0x37/0x42
[42949373.800000] 08323fe0:  [<0805b49d>] new_thread_handler+0x57/0x7e
[42949373.800000] 08323ffc:  [<a55a5a5a>] 0xa55a5a5a
[42949373.800000] 
Segmentation fault
```

Could anyone here tell me what happened ? I really need your help guys..

THank you :popcorn:

---

