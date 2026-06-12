---
title: "Switching virtual terminals causes X to restart"
date: 2007-10-16
forum: Desktop Environments
---

### Post by rickg100 on 2007-10-16
Hi All,

I'm using v6.10, but have had the same problem in 2 previous versions (I think 6.04, and 5.10).

Here's the situation. 
1) I log into my X session. 
2) I swtich to a different virtual terminal say <ctrl>+<alt>+F1
3) that switches fine and I'm in the text based terminal
4) Now I try to switch back to the x-session on <ctrl>+<alt>+F7
5) It switch back to X, but my x-session restarts and I'm back at the X login screen.

Obviously, I would like my session to still be active when I switch back to the x-terminal.

Same thing happens if I "suspend" and "resume" - that causes X to restart.

Any suggestions would be greatly appreciated.

Thanks

-Rick

---

### Post by lucho64 on 2007-10-17
Any clue in the log files? /var/log/Xorg.0.log

---

### Post by rickg100 on 2007-10-19
Here are the additions (and attached) to the Xorg log when I switch virtual terminals.

------------------
AUDIT: Fri Oct 19 11:08:01 2007: 4869 X: client 2 rejected from local host
AUDIT: Fri Oct 19 11:08:01 2007: 4869 X: client 4 rejected from local host
AUDIT: Fri Oct 19 11:08:01 2007: 4869 X: client 3 rejected from local host
AUDIT: Fri Oct 19 11:08:01 2007: 4869 X: client 5 rejected from local host
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
        the saved state
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(WW) I810(0): Successfully set original devices (2)
(II) Open ACPI successful (/var/run/acpid.socket)
(II) I810(0): Detected resume, re-POSTing.
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): Re-POSTing via int10.
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x000df000 (pgoffset 223)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x07fff000 (pgoffset 32767)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x07ffb000 (pgoffset 32763)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x07fea000 (pgoffset 32746)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x07ffa000 (pgoffset 32762)
(WW) I810(0): PGTBL_ER is 0x00000029

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers/i810_drv.so [0xb7b8b5b6]
3: /usr/lib/xorg/modules/libxaa.so [0xb79a3ec2]
4: /usr/X11R6/bin/X [0x80cbe7c]
5: /usr/X11R6/bin/X [0x80d9718]
6: /usr/X11R6/bin/X(xf86Wakeup+0x3bd) [0x80c508d]
7: /usr/X11R6/bin/X(WakeupHandler+0x59) [0x808a5c9]
8: /usr/X11R6/bin/X(WaitForSomething+0x1b9) [0x81944f9]
9: /usr/X11R6/bin/X(Dispatch+0x82) [0x8086832]
10: /usr/X11R6/bin/X(main+0x485) [0x806e715]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d178cc]
12: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
        the saved state
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(WW) I810(0): Successfully set original devices (2)
-------------

Thanks

-Rick

---

### Post by rickg100 on 2007-10-19
Well, I wouldn't say the problem is resolved, but I did just upgrade to 7.10 and things seems to be working now.

---

