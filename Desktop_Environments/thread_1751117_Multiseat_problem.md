---
title: "Multiseat problem"
date: 2011-05-06
forum: Desktop Environments
---

### Post by Fisher on 2011-05-06
Hello.
I had a multiseat configured pc for a long time.
It's a Semprom 2.4, with 2 nvidia cards, was working well, but too slow.
I decided to upgrade. Got a Asus M2N-SLI Deluxe NForce 570 SLI Chipset, with a Phenon 9750 processor, 4GB of Mushkin DDR2 800 memory, 2X Geforce 7200GS 256MB, Ubuntu Linux 10.04 LTS up to date with Nvidia-173 drivers.
The 173 was the only drivers that at least made both seats work, at least for a while.
The seats start normally, then, after some small time it simply locks up!
I can however access my pc through ssh and this is what I get from dmesg:

[ 160.834800] NVRM: Xid (0004:00): 26, Ch 00000000 M 00001818 D 3f800000 intr ffffffff
[ 160.837629] NVRM: Xid (0004:00): 1, Ch 00000000 M 00001818 D 3f800000 intr ffffffff
[ 164.928637] NVRM: Xid (0002:00): 26, Ch 00000000 M 00000464 D ff4a3f38 intr ffffffff
[ 164.931643] NVRM: Xid (0002:00): 1, Ch 00000000 M 00000464 D ff4a3f38 intr ffffffff
[ 173.684548] NVRM: Xid (0002:00): 16, Head 00000000 Count 000040a3
[ 173.876053] NVRM: Xid (0004:00): 8, Channel 00000002
[ 173.877650] NVRM: Xid (0004:00): 16, Head 00000000 Count 0000411b
[ 173.877664] NVRM: Xid (0004:00): 16, Head 00000001 Count 000027a6
[ 178.684093] NVRM: Xid (0002:00): 8, Channel 00000020
[ 181.688566] NVRM: Xid (0002:00): 16, Head 00000000 Count 000040a4
[ 181.880068] NVRM: Xid (0004:00): 16, Head 00000000 Count 0000411c
[ 181.880099] NVRM: Xid (0004:00): 16, Head 00000001 Count 000027a7
[ 186.684096] NVRM: Xid (0002:00): 8, Channel 0000001e
[ 189.692566] NVRM: Xid (0002:00): 16, Head 00000000 Count 000040a5
[ 189.876127] NVRM: Xid (0004:00): 16, Head 00000000 Count 0000411d
[ 194.692095] NVRM: Xid (0002:00): 8, Channel 00000020
[ 360.496041] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 360.496047] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 360.496052] Xorg D 00011c60 0 1302 1148 0x00400004
[ 360.496062] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 360.496073] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 360.496083] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 360.496095] Call Trace:
[ 360.496107] [<c03e3d3f>] vga_get+0xdf/0x150
[ 360.496117] [<c014d460>] ? default_wake_function+0x0/0x20
[ 360.496125] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 360.496133] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 360.496141] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 360.496146] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 360.496152] [<c02143e2>] sys_write+0x42/0x70
[ 360.496158] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 480.496041] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 480.496048] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 480.496053] Xorg D 00011c60 0 1302 1148 0x00400004
[ 480.496063] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 480.496078] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 480.496090] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 480.496100] Call Trace:
[ 480.496112] [<c03e3d3f>] vga_get+0xdf/0x150
[ 480.496122] [<c014d460>] ? default_wake_function+0x0/0x20
[ 480.496130] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 480.496141] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 480.496148] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 480.496153] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 480.496159] [<c02143e2>] sys_write+0x42/0x70
[ 480.496165] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 600.496040] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 600.496047] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 600.496052] Xorg D 00011c60 0 1302 1148 0x00400004
[ 600.496061] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 600.496075] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 600.496085] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 600.496094] Call Trace:
[ 600.496106] [<c03e3d3f>] vga_get+0xdf/0x150
[ 600.496116] [<c014d460>] ? default_wake_function+0x0/0x20
[ 600.496124] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 600.496133] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 600.496140] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 600.496145] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 600.496151] [<c02143e2>] sys_write+0x42/0x70
[ 600.496157] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 720.495826] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 720.495832] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 720.495837] Xorg D 00011c60 0 1302 1148 0x00400004
[ 720.495846] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 720.495857] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 720.495866] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 720.495879] Call Trace:
[ 720.495891] [<c03e3d3f>] vga_get+0xdf/0x150
[ 720.495900] [<c014d460>] ? default_wake_function+0x0/0x20
[ 720.495908] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 720.495916] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 720.495924] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 720.495929] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 720.495935] [<c02143e2>] sys_write+0x42/0x70
[ 720.495940] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 840.492050] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 840.492057] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 840.492062] Xorg D 00011c60 0 1302 1148 0x00400004
[ 840.492071] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 840.492084] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 840.492094] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 840.492105] Call Trace:
[ 840.492117] [<c03e3d3f>] vga_get+0xdf/0x150
[ 840.492127] [<c014d460>] ? default_wake_function+0x0/0x20
[ 840.492135] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 840.492143] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 840.492151] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 840.492156] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 840.492165] [<c02143e2>] sys_write+0x42/0x70
[ 840.492170] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 960.492051] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 960.492058] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 960.492063] Xorg D 00011c60 0 1302 1148 0x00400004
[ 960.492072] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 960.492087] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 960.492099] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 960.492111] Call Trace:
[ 960.492123] [<c03e3d3f>] vga_get+0xdf/0x150
[ 960.492132] [<c014d460>] ? default_wake_function+0x0/0x20
[ 960.492140] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 960.492151] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 960.492159] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 960.492164] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 960.492174] [<c02143e2>] sys_write+0x42/0x70
[ 960.492180] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 1080.496042] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 1080.496048] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 1080.496053] Xorg D 00011c60 0 1302 1148 0x00400004
[ 1080.496062] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 1080.496073] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 1080.496086] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 1080.496097] Call Trace:
[ 1080.496109] [<c03e3d3f>] vga_get+0xdf/0x150
[ 1080.496119] [<c014d460>] ? default_wake_function+0x0/0x20
[ 1080.496127] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 1080.496138] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 1080.496146] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 1080.496151] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 1080.496159] [<c02143e2>] sys_write+0x42/0x70
[ 1080.496165] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 1200.492049] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 1200.492055] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 1200.492060] Xorg D 00011c60 0 1302 1148 0x00400004
[ 1200.492070] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 1200.492081] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 1200.492091] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 1200.492102] Call Trace:
[ 1200.492115] [<c03e3d3f>] vga_get+0xdf/0x150
[ 1200.492125] [<c014d460>] ? default_wake_function+0x0/0x20
[ 1200.492132] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 1200.492143] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 1200.492151] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 1200.492155] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 1200.492161] [<c02143e2>] sys_write+0x42/0x70
[ 1200.492167] [<c01096c3>] sysenter_do_call+0x12/0x28
[ 1320.492047] INFO: task Xorg:1302 blocked for more than 120 seconds.
[ 1320.492053] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 1320.492058] Xorg D 00011c60 0 1302 1148 0x00400004
[ 1320.492067] f14f1ee0 00203086 00000004 00011c60 00000000 c08914c0 f14028e4 c08914c0
[ 1320.492080] 7bfe4505 00000028 c08914c0 c08914c0 f14028e4 c08914c0 c08914c0 f1631c00
[ 1320.492092] 7bfcfdf1 00000028 f1402640 f7644800 f1402640 f1402640 f14f1f18 c03e3d3f
[ 1320.492106] Call Trace:
[ 1320.492118] [<c03e3d3f>] vga_get+0xdf/0x150
[ 1320.492128] [<c014d460>] ? default_wake_function+0x0/0x20
[ 1320.492136] [<c03e3e43>] vga_arb_write+0x93/0x530
[ 1320.492147] [<c03010f4>] ? security_file_permission+0x14/0x20
[ 1320.492154] [<c0213af2>] vfs_write+0xa2/0x1a0
[ 1320.492159] [<c03e3db0>] ? vga_arb_write+0x0/0x530
[ 1320.492165] [<c02143e2>] sys_write+0x42/0x70
[ 1320.492171] [<c01096c3>] sysenter_do_call+0x12/0x28

I then need to reboot, so I can access the gui again.
Any ideas of what I can do??

Thanks

---

### Post by Fisher on 2011-05-06
Solved my problem!!
Very weird solution...
Changed both videocards to a GeForce 8400 GS and a GeForce 8500 GT, installed nvidia-current and all works like a charm.
I would like to know why it wsa not working before... I even have tried the nvidia-current with the other cards and got initialisation errors on them.

Thaks for everybody that at least have read this thread!!!

---

