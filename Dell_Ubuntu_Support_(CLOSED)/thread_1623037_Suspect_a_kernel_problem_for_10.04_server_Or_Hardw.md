---
title: "Suspect a kernel problem for 10.04 server Or Hardware problem for our new Dells"
date: 2010-11-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 30miles on 2010-11-16
we have two new Dell i7 computer run on 10.04 server for web servers.  Recently they always dead randomly. there was no error messages in log  files. The PING does not work. the power was still on. The only way to  reboot them are to shutdown the power.

Until yesterday, we catch our first error message. As listed in the  follow.   the problem we suspect is a kernel problem. The kernel version  is 2.6.32-24. Also it could be the hardware problem. I am going to do a  memory test soon. 

Is there any advise???? Thank you very much ....

Nov 16 05:04:48 stork kernel: [125990.284892] BUG: Bad page map in process apache2  pte:800011006f6ba047 pmd:13820c067
Nov 16 05:04:48 stork kernel: [125990.285212] addr:00007f8621851000 vm_flags:00100073 anon_vma:ffff88013880fda0 mapping:sad:null) index:7f8621851
Nov 16 05:04:48 stork kernel: [125990.285587] Pid: 1393, comm: apache2 Not tainted 2.6.32-24-server #43-Ubuntu
Nov 16 05:04:48 stork kernel: [125990.285591] Call Trace:
Nov 16 05:04:48 stork kernel: [125990.285602]  [<ffffffff81111672>] print_bad_pte+0x1d2/0x280
Nov 16 05:04:48 stork kernel: [125990.285609]  [<ffffffff8113e742>] ? __mem_cgroup_uncharge_common+0x162/0x220
Nov 16 05:04:48 stork kernel: [125990.285615]  [<ffffffff8111178c>] vm_normal_page+0x6c/0x70
Nov 16 05:04:48 stork kernel: [125990.285619]  [<ffffffff81111d7f>] zap_pte_range+0x1ff/0x400
Nov 16 05:04:48 stork kernel: [125990.285625]  [<ffffffff81112e65>] unmap_page_range+0x1c5/0x2a0
Nov 16 05:04:48 stork kernel: [125990.285630]  [<ffffffff81113688>] unmap_vmas+0x178/0x310
Nov 16 05:04:48 stork kernel: [125990.285637]  [<ffffffff8111807b>] exit_mmap+0xbb/0x190
Nov 16 05:04:48 stork kernel: [125990.285643]  [<ffffffff81064c12>] mmput+0x42/0x110
Nov 16 05:04:48 stork kernel: [125990.285649]  [<ffffffff8106b092>] exit_mm+0x112/0x150
Nov 16 05:04:48 stork kernel: [125990.285655]  [<ffffffff8155aa35>] ? _spin_lock_irq+0x15/0x20
Nov 16 05:04:48 stork kernel: [125990.285660]  [<ffffffff8106b305>] do_exit+0x125/0x380
Nov 16 05:04:48 stork kernel: [125990.285664]  [<ffffffff8155aaee>] ? _spin_lock+0xe/0x20
Nov 16 05:04:48 stork kernel: [125990.285669]  [<ffffffff8106b5b5>] do_group_exit+0x55/0xd0
Nov 16 05:04:48 stork kernel: [125990.285676]  [<ffffffff8107bdf7>] get_signal_to_deliver+0x1d7/0x3d0
Nov 16 05:04:48 stork kernel: [125990.285684]  [<ffffffff81012a25>] do_signal+0x75/0x1c0
Nov 16 05:04:48 stork kernel: [125990.285691]  [<ffffffff81157a98>] ? d_free+0x58/0x60
Nov 16 05:04:48 stork kernel: [125990.285696]  [<ffffffff81098b69>] ? do_futex+0xc9/0x1b0
Nov 16 05:04:48 stork kernel: [125990.285702]  [<ffffffff81012bcd>] do_notify_resume+0x5d/0x80
Nov 16 05:04:48 stork kernel: [125990.285707]  [<ffffffff8101347e>] int_signal+0x12/0x17
Nov 16 05:04:48 stork kernel: [125990.285711] Disabling lock debugging due to kernel taint
Nov 16 05:04:48 stork kernel: [125990.285716] BUG: Bad page map in process apache2  pte:8000030092b8d047 pmd:13820c067
Nov 16 05:04:48 stork kernel: [125990.286028] addr:00007f8621855000 vm_flags:00100073 anon_vma:ffff88013880fda0 mapping:sad:null) index:7f8621855
Nov 16 05:04:48 stork kernel: [125990.286448] Pid: 1393, comm: apache2 Tainted: G    B      2.6.32-24-server #43-Ubuntu
Nov 16 05:04:48 stork kernel: [125990.286452] Call Trace:
Nov 16 05:04:48 stork kernel: [125990.286456]  [<ffffffff81111672>] print_bad_pte+0x1d2/0x280
Nov 16 05:04:48 stork kernel: [125990.286461]  [<ffffffff8113e742>] ? __mem_cgroup_uncharge_common+0x162/0x220
Nov 16 05:04:48 stork kernel: [125990.286467]  [<ffffffff8111178c>] vm_normal_page+0x6c/0x70
Nov 16 05:04:48 stork kernel: [125990.286472]  [<ffffffff81111d7f>] zap_pte_range+0x1ff/0x400
Nov 16 05:04:48 stork kernel: [125990.286477]  [<ffffffff81112e65>] unmap_page_range+0x1c5/0x2a0
Nov 16 05:04:48 stork kernel: [125990.286482]  [<ffffffff81113688>] unmap_vmas+0x178/0x310
Nov 16 05:04:48 stork kernel: [125990.286488]  [<ffffffff8111807b>] exit_mmap+0xbb/0x190
Nov 16 05:04:48 stork kernel: [125990.286492]  [<ffffffff81064c12>] mmput+0x42/0x110
Nov 16 05:04:48 stork kernel: [125990.286497]  [<ffffffff8106b092>] exit_mm+0x112/0x150
Nov 16 05:04:48 stork kernel: [125990.286502]  [<ffffffff8155aa35>] ? _spin_lock_irq+0x15/0x20
Nov 16 05:04:48 stork kernel: [125990.286507]  [<ffffffff8106b305>] do_exit+0x125/0x380
Nov 16 05:04:48 stork kernel: [125990.286511]  [<ffffffff8155aaee>] ? _spin_lock+0xe/0x20
Nov 16 05:04:48 stork kernel: [125990.286516]  [<ffffffff8106b5b5>] do_group_exit+0x55/0xd0
Nov 16 05:04:48 stork kernel: [125990.286522]  [<ffffffff8107bdf7>] get_signal_to_deliver+0x1d7/0x3d0
Nov 16 05:04:48 stork kernel: [125990.286527]  [<ffffffff81012a25>] do_signal+0x75/0x1c0
Nov 16 05:04:48 stork kernel: [125990.286533]  [<ffffffff81157a98>] ? d_free+0x58/0x60
Nov 16 05:04:48 stork kernel: [125990.286537]  [<ffffffff81098b69>] ? do_futex+0xc9/0x1b0
Nov 16 05:04:48 stork kernel: [125990.286543]  [<ffffffff81012bcd>] do_notify_resume+0x5d/0x80
Nov 16 05:04:48 stork kernel: [125990.286548]  [<ffffffff8101347e>] int_signal+0x12/0x17
Nov 16 05:04:48 stork kernel: [125990.286552] BUG: Bad page map in process apache2  pte:8000f300ba1b3047 pmd:13820c067
Nov 16 05:04:48 stork kernel: [125990.286862] addr:00007f8621856000 vm_flags:00100073 anon_vma:ffff88013880fda0 mapping:sad:null) index:7f8621856
Nov 16 05:04:48 stork kernel: [125990.287231] Pid: 1393, comm: apache2 Tainted: G    B      2.6.32-24-server #43-Ubuntu
Nov 16 05:04:48 stork kernel: [125990.287234] Call Trace:
Nov 16 05:04:48 stork kernel: [125990.287238]  [<ffffffff81111672>] print_bad_pte+0x1d2/0x280
Nov 16 05:04:48 stork kernel: [125990.287243]  [<ffffffff8113e742>] ? __mem_cgroup_uncharge_common+0x162/0x220
Nov 16 05:04:48 stork kernel: [125990.287249]  [<ffffffff8111178c>] vm_normal_page+0x6c/0x70
Nov 16 05:04:48 stork kernel: [125990.287253]  [<ffffffff81111d7f>] zap_pte_range+0x1ff/0x400
Nov 16 05:04:48 stork kernel: [125990.287259]  [<ffffffff81112e65>] unmap_page_range+0x1c5/0x2a0
Nov 16 05:04:48 stork kernel: [125990.287264]  [<ffffffff81113688>] unmap_vmas+0x178/0x310
Nov 16 05:04:48 stork kernel: [125990.287269]  [<ffffffff8111807b>] exit_mmap+0xbb/0x190
Nov 16 05:04:48 stork kernel: [125990.287274]  [<ffffffff81064c12>] mmput+0x42/0x110
Nov 16 05:04:48 stork kernel: [125990.287279]  [<ffffffff8106b092>] exit_mm+0x112/0x150
Nov 16 05:04:48 stork kernel: [125990.287283]  [<ffffffff8155aa35>] ? _spin_lock_irq+0x15/0x20
Nov 16 05:04:48 stork kernel: [125990.287289]  [<ffffffff8106b305>] do_exit+0x125/0x380
Nov 16 05:04:48 stork kernel: [125990.287293]  [<ffffffff8155aaee>] ? _spin_lock+0xe/0x20
Nov 16 05:04:48 stork kernel: [125990.287298]  [<ffffffff8106b5b5>] do_group_exit+0x55/0xd0
Nov 16 05:04:48 stork kernel: [125990.287303]  [<ffffffff8107bdf7>] get_signal_to_deliver+0x1d7/0x3d0
Nov 16 05:04:48 stork kernel: [125990.287309]  [<ffffffff81012a25>] do_signal+0x75/0x1c0
Nov 16 05:04:48 stork kernel: [125990.287314]  [<ffffffff81157a98>] ? d_free+0x58/0x60
Nov 16 05:04:48 stork kernel: [125990.287319]  [<ffffffff81098b69>] ? do_futex+0xc9/0x1b0
Nov 16 05:04:48 stork kernel: [125990.287324]  [<ffffffff81012bcd>] do_notify_resume+0x5d/0x80
Nov 16 05:04:48 stork kernel: [125990.287330]  [<ffffffff8101347e>] int_signal+0x12/0x17

---

### Post by 30miles on 2010-11-17
I think i have found the solution. the 10.04.1 update may fix the  problem. I have updated them all. Hopefully they should be find.

---

