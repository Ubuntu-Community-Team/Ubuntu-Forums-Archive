---
title: "Kernel panic - not syncing: Attempted to kill init!"
date: 2008-12-07
forum: General Help
---

### Post by elraymundo on 2008-12-07
Hello everyone,

New Linux user here.

My Ubuntu 8 Hardy Heron machine does not boot and gives me the following error:

*Kernel panic - not syncing: Attempted to kill init!*

I have no idea what to do. I rebooted the machine twice and it stops the boot process at the same point every time.

This is not a new installation. I've had the machine up and running for a couple of months, nor is this the first time the machine has been rebooted. As far as I know, no changes were made (other than the common updates made when the system prompted me to). No new hardware has been installed or reconfigured and I have made no changes to the OS.

Can someone help me understand what I should do to fix this problem? I can provide more information if given guidance on what information to provide.

Here is a copy of what I see on my screen:

[I][24.561208] Call Trace:
[24.561295] [<c02661ab>] write_chan+0xfb/0x350
[24.561387] [<c0125f80>] default_wake_function+0x0/0x10
[24.561480] [<c0263a96>] tty_write+0x146/0x1e0
[24.561580] [<c02660b0>] write_chan+0x0/0x350
[24.561679] [<c02644d9>] redirected_tty_write+0x29/0xa0
[24.561780] [<c02644b0>] redirected_tty_write+0x0/0xa0
[24.561881] [<c0192179>] vfs_write+0xb9/0x170
[24.561981] [<c01928b1>] sys_write+0x41/0x70
[24.562080] [<c0104432>] syscall_call+0x7/0xb
[24.562180] [<c0310000>] unix_destruct_fds+0x40/0x50
[24.562280] =======================
[24.562336] Code: ce 4e c0 c3 a1 4c be 4e c0 89 02 a1 00 ce 4e c0 c3 8d b4 26
 00 00 00 00 8d bc 27 00 00 00 00 0f b6 80 c8 00 00 00 83 e0 01 3c 01 <19> 00 25
 00 10 00 00 c3 8d b6 00 00 00 00 8d bf 00 00 00 00 31
[24.565140] EIP: [<c026f23c>] con_write_room+0xc/0x20 SS:ESP 0068:f7c65f14
[24.565298] ---[ end trace 846079fa38e90cc6 ]---
[24.565335] Kernel panic - not syncing: Attempted to kill init!
[/I]
Thanks!!

Ok, strangely enough, I rebooted the system again (for the second or third time) and I got past the "Kernel panic - not syncing: Attempted to kill init!" message and twice got "Fixing recursive..." something (accidentally closed the Notepad I wrote the message on before saving it) and then the third reboot got me to a login prompt. I have no idea what fixed the problem. Anyone have any ideas?

---

