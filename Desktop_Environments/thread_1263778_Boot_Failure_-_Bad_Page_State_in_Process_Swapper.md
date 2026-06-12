---
title: "Boot Failure - Bad Page State in Process Swapper"
date: 2009-09-11
forum: Desktop Environments
---

### Post by linux4me on 2009-09-11
I'm running Ubuntu 9.04 64-bit with the 2.6.28-15-generic kernel installed using the Alternate CD and LVM encryption. It has been working flawlessly for months, but today when I tried to boot it up, I got errors like:
> Fixing recursive fault but reboot is needed... and > bad page state in process swapper

I get to the screen where I enter the encryption passphrase, and it tells me the disk was unlocked successfully, but then the screen goes black and the system doesn't boot.

I tried booting using recovery mode, but got no further.

I tried starting with a Live CD of 8.04 i386, but it goes directly into intramfs when I choose to run it without installing so I haven't been able to get a terminal window. I'm downloading a 9.04 AMD 64 Live CD at the moment to see if it will work to get me a terminal window.

I'm running Memtest on the machine at the moment, but it hasn't found any errors. I haven't installed anything new or needed to run any updates since the last normal boot (yesterday).

I haven't been able to find anything in Google or in the forums about this error to help me get past it.

Can anyone give me some help?

TIA

---

### Post by linux4me on 2009-09-11
I *think* I found the problem. I was thinking the error was due to a problem with my swap file, but it looks like it was memory related.

Memtest showed a bunch of errors in the 8xxxx.xx MB range (the machine has four, 2 GB RAM sticks in it), so I pulled out the last RAM stick and it booted fine after checking the disk. 

I still have my fingers crossed.

---

### Post by egarland on 2010-02-14
For me it was fried RAM.  Memtest86 showed errors.  Replaced the first stick and the machine boots normally now.

---

### Post by linux4me on 2010-02-14
Yeah, that's what it was in my case, too. I got a replacement stick for the one memtest indicated was bad, and since replacing it I haven't had any more problems.

---

### Post by phattymatty on 2010-02-18
I had a similar issue... in my case, the system would boot and run for about 10 minutes and then freeze. Dumping kern.log produced this error:

Feb 17 12:02:00 s1 kernel: [  403.105092] Bad page state in process 'swapper'
Feb 17 12:02:00 s1 kernel: [  403.105093] page:ffffe200076860f8 flags:0x8000000000000000 mapping:0a00000000000000 mapcount:0 count:0
Feb 17 12:02:00 s1 kernel: [  403.105097] Trying to fix it up, but a reboot is needed
Feb 17 12:02:00 s1 kernel: [  403.105098] Backtrace:
Feb 17 12:02:00 s1 kernel: [  403.105100] Pid: 0, comm: swapper Not tainted 2.6.28-18-server #59-Ubuntu
Feb 17 12:02:00 s1 kernel: [  403.105102] Call Trace:
Feb 17 12:02:00 s1 kernel: [  403.105104]  <IRQ>  [<ffffffff802b605b>] bad_page+0x6b/0xa0
Feb 17 12:02:00 s1 kernel: [  403.105112]  [<ffffffff802b7413>] free_hot_cold_page+0x263/0x270
Feb 17 12:02:00 s1 kernel: [  403.105115]  [<ffffffff802b748b>] free_hot_page+0xb/0x10
Feb 17 12:02:00 s1 kernel: [  403.105118]  [<ffffffff802ba45f>] put_page+0x5f/0x110

After troubleshooting and running memtest86, clearly the problem lied in the memory.  I am running 4 x 2GB DDR2 @ 2.10V.  Long story short, I resolved the problem by examining the memory voltage settings in the BIOS.  The settings had been reset or incorrectly set to run @ 1.8V.  Increasing the voltage to 2.10 volts, which the memory called for, fixed the problem.  Before writing the memory off as bad memory, try increasing your voltage and interrogating your power supply as a possible troublemaker.

---

### Post by linux4me on 2010-02-18
@Phatty, it's interesting that voltages could result in the same error. Based on your experience, the RAM voltages are certainly worth checking since many RAM sticks are designed to run at different voltages than those the BIOS defaults to.

In my case, I'm pretty sure it was just a bad memory stick. The voltages were set to manufacturer's specs and there have been no further problems since I replaced the bad RAM back in September. (Fingers crossed.)

---

### Post by kvarley on 2010-04-20
Thank you for the information. I noticed that my motherboard was set to supply 1.8v when my RAM was labelled 2.1v

I have bumped it up and will reply with my results.

---

