---
title: "Most recent kernel update crashed Virtualbox"
date: 2024-08-14
forum: Desktop Environments
---

### Post by agw-4774 on 2024-08-14
7.901224] UBSAN: array-index-out-of-bounds in /var/lib/dkms/virtualbox/6.1.50/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:577:45
Aug 11 12:53:42 a kernel: [    7.901227] index 3 is out of range for type 'page *[1]'
Aug 11 12:53:42 a kernel: [    7.901228] CPU: 20 PID: 1743 Comm: modprobe Tainted: P           OE      6.5.0-45-generic #45~22.04.1-Ubuntu
Aug 11 12:53:42 a kernel: [    7.901231] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./X570 Phantom Gaming 4, BIOS P3.40 10/21/2020
Aug 11 12:53:42 a kernel: [    7.901232] Call Trace:
Aug 11 12:53:42 a kernel: [    7.901233]  <TASK>
Aug 11 12:53:42 a kernel: [    7.901235]  dump_stack_lvl+0x48/0x70
Aug 11 12:53:42 a kernel: [    7.901238]  dump_stack+0x10/0x20
Aug 11 12:53:42 a kernel: [    7.901241]  __ubsan_handle_out_of_bounds+0xc6/0x110
Aug 11 12:53:42 a kernel: [    7.901245]  rtR0MemObjLinuxVMap+0xb7/0xc0 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901269]  rtR0MemObjNativeAllocCont+0x6e/0x120 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901293]  VBoxHost_RTR0MemObjAllocContTag+0x61/0xa0 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901316]  supdrvGipCreate+0x66/0xdf0 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901340]  ? srso_return_thunk+0x5/0x10
Aug 11 12:53:42 a kernel: [    7.901343]  ? rtR0MemAllocEx+0xee/0x160 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901367]  ? srso_return_thunk+0x5/0x10
Aug 11 12:53:42 a kernel: [    7.901371]  supdrvInitDevExt+0x14d/0x330 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901395]  VBoxDrvLinuxInit+0x67/0xff0 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901418]  ? __pfx_VBoxDrvLinuxInit+0x10/0x10 [vboxdrv]
Aug 11 12:53:42 a kernel: [    7.901440]  do_one_initcall+0x5e/0x340
Aug 11 12:53:42 a kernel: [    7.901445]  do_init_module+0x68/0x260
Aug 11 12:53:42 a kernel: [    7.901449]  load_module+0xb85/0xcd0
Aug 11 12:53:42 a kernel: [    7.901456]  init_module_from_file+0x96/0x100
Aug 11 12:53:42 a kernel: [    7.901459]  ? init_module_from_file+0x96/0x100
Aug 11 12:53:42 a kernel: [    7.901466]  idempotent_init_module+0x11c/0x2b0
Aug 11 12:53:42 a kernel: [    7.901471]  __x64_sys_finit_module+0x64/0xd0
Aug 11 12:53:42 a kernel: [    7.901475]  x64_sys_call+0x130f/0x20b0
Aug 11 12:53:42 a kernel: [    7.901477]  do_syscall_64+0x55/0x90
Aug 11 12:53:42 a kernel: [    7.901479]  ? do_syscall_64+0x61/0x90
Aug 11 12:53:42 a kernel: [    7.901482]  entry_SYSCALL_64_after_hwframe+0x73/0xdd
Aug 11 12:53:42 a kernel: [    7.901484] RIP: 0033:0x70a1b811e88d
Aug 11 12:53:42 a kernel: [    7.901489] Code: 5b 41 5c c3 66 0f 1f 84 00 00 00 00 00 f3 0f 1e fa 48 89 f8 48 89 f7 48 89 d6 48 89 ca 4d 89 c2 4d 89 c8 4c 8b 4c 24 08 0f 05 <48> 3d 01 f0 ff ff 73 01 c3 48 8b 0d 73 b5 0f 00 f7 d8 64 89 01 48
Aug 11 12:53:42 a kernel: [    7.901490] RSP: 002b:00007ffe879c8818 EFLAGS: 00000246 ORIG_RAX: 0000000000000139
Aug 11 12:53:42 a kernel: [    7.901493] RAX: ffffffffffffffda RBX: 000055579381cbd0 RCX: 000070a1b811e88d
Aug 11 12:53:42 a kernel: [    7.901494] RDX: 0000000000000000 RSI: 0000555791940cd2 RDI: 0000000000000003
Aug 11 12:53:42 a kernel: [    7.901496] RBP: 0000000000040000 R08: 0000000000000000 R09: 00007ffe879c8950
Aug 11 12:53:42 a kernel: [    7.901497] R10: 0000000000000003 R11: 0000000000000246 R12: 0000555791940cd2
Aug 11 12:53:42 a kernel: [    7.901499] R13: 000055579381c6a0 R14: 000055579381c680 R15: 000055579381cee0

---

### Post by currentshaft on 2024-08-14
..

---

### Post by ActionParsnip on 2024-08-16
I suggest you report a bug

---

