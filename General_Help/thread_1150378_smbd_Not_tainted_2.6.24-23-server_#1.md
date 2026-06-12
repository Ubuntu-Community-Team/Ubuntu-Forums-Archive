---
title: "smbd Not tainted 2.6.24-23-server #1"
date: 2009-05-06
forum: General Help
---

### Post by doctordope on 2009-05-06
Any idea why this keeps crashing . 

May  5 21:25:43 babyjesus kernel: [700067.811897] Pid: 475, comm: smbd Not tainted 2.6.24-23-server #1
May  5 21:25:43 babyjesus kernel: [700067.811899] 
May  5 21:25:43 babyjesus kernel: [700067.811899] Call Trace:
May  5 21:25:43 babyjesus kernel: [700067.811926]  [bad_page+0x60/0xa0] bad_page+0x60/0xa0
May  5 21:25:43 babyjesus kernel: [700067.811932]  [get_page_from_freelist+0x5ec/0x6c0] get_page_from_freelist+0x5ec/0x6c0
May  5 21:25:43 babyjesus kernel: [700067.811945]  [__alloc_pages+0x9d/0x3d0] __alloc_pages+0x9d/0x3d0
May  5 21:25:43 babyjesus kernel: [700067.811955]  [ext3:__get_free_pages+0xe/0x1320] __get_free_pages+0xe/0x40
May  5 21:25:43 babyjesus kernel: [700067.811959]  [copy_process+0xe2/0x1500] copy_process+0xe2/0x1500
May  5 21:25:43 babyjesus kernel: [700067.811968]  [sys_accept+0x16f/0x200] sys_accept+0x16f/0x200
May  5 21:25:43 babyjesus kernel: [700067.811975]  [system_call+0x7e/0x83] system_call+0x7e/0x83
May  5 21:25:43 babyjesus kernel: [700067.811978]  [do_fork+0x48/0x2a0] do_fork+0x48/0x2a0
May  5 21:25:43 babyjesus kernel: [700067.811984]  [sys_select+0x44/0x1c0] sys_select+0x44/0x1c0
May  5 21:25:43 babyjesus kernel: [700067.811989]  [ptregscall_common+0x67/0xb0] ptregscall_common+0x67/0xb0
May  5 21:25:43 babyjesus kernel: [700067.811999] 
May  5 21:25:43 babyjesus kernel: [700067.913014] Bad page state in process 'swapper'
May  5 21:25:43 babyjesus kernel: [700067.913016] page:ffff81006e75b0a8 flags:0x0000000000010028 mapping:ffff81006dc13ad8 mapcount:0 count:1
May  5 21:25:43 babyjesus kernel: [700067.913018] Trying to fix it up, but a reboot is needed
May  5 21:25:43 babyjesus kernel: [700067.913019] Backtrace:
May  5 21:25:43 babyjesus kernel: [700067.913104] Pid: 0, comm: swapper Tainted: G    B   2.6.24-23-server #1
May  5 21:25:43 babyjesus kernel: [700067.913106] 
May  5 21:25:43 babyjesus kernel: [700067.913106] Call Trace:
May  5 21:25:43 babyjesus kernel: [700067.913109]  <IRQ>  [enqueue_task+0x13/0x30] enqueue_task+0x13/0x30
May  5 21:25:43 babyjesus kernel: [700067.913136]  [bad_page+0x60/0xa0] bad_page+0x60/0xa0
May  5 21:25:43 babyjesus kernel: [700067.913140]  [__free_pages_ok+0x351/0x380] __free_pages_ok+0x351/0x380
May  5 21:25:43 babyjesus kernel: [700067.913146]  [free_task+0x1e/0x30] free_task+0x1e/0x30
May  5 21:25:43 babyjesus kernel: [700067.913151]  [__rcu_process_callbacks+0x86/0x1f0] __rcu_process_callbacks+0x86/0x1f0
May  5 21:25:43 babyjesus kernel: [700067.913156]  [rcu_process_callbacks+0x23/0x50] rcu_process_callbacks+0x23/0x50
May  5 21:25:43 babyjesus kernel: [700067.913160]  [tasklet_action+0x49/0xb0] tasklet_action+0x49/0xb0
May  5 21:25:43 babyjesus kernel: [700067.913164]  [__do_softirq+0x75/0xe0] __do_softirq+0x75/0xe0
May  5 21:25:43 babyjesus kernel: [700067.913168]  [tick_program_event+0x35/0x60] tick_program_event+0x35/0x60
May  5 21:25:43 babyjesus kernel: [700067.913174]  [call_softirq+0x1c/0x30] call_softirq+0x1c/0x30
May  5 21:25:43 babyjesus kernel: [700067.913178]  [do_softirq+0x35/0x90] do_softirq+0x35/0x90
May  5 21:25:43 babyjesus kernel: [700067.913181]  [irq_exit+0x88/0x90] irq_exit+0x88/0x90
May  5 21:25:43 babyjesus kernel: [700067.913186]  [smp_apic_timer_interrupt+0x46/0x70] smp_apic_timer_interrupt+0x46/0x70
May  5 21:25:43 babyjesus kernel: [700067.913190]  [default_idle+0x0/0x40] default_idle+0x0/0x40
May  5 21:25:43 babyjesus kernel: [700067.913192]  [default_idle+0x0/0x40] default_idle+0x0/0x40
May  5 21:25:43 babyjesus kernel: [700067.913195]  [apic_timer_interrupt+0x66/0x70] apic_timer_interrupt+0x66/0x70
May  5 21:25:43 babyjesus kernel: [700067.913197]  <EOI>  [default_idle+0x29/0x40] default_idle+0x29/0x40
May  5 21:25:43 babyjesus kernel: [700067.913207]  [cpu_idle+0x48/0xe0] cpu_idle+0x48/0xe0
May  5 21:25:43 babyjesus kernel: [700067.913212]  [start_kernel+0x2c5/0x350] start_kernel+0x2c5/0x350
May  5 21:25:43 babyjesus kernel: [700067.913217]  [x86_64_start_kernel+0x12e/0x140] _sinittext+0x12e/0x140
May  5 21:25:43 babyjesus kernel: [700067.913222] 
(END)

---

