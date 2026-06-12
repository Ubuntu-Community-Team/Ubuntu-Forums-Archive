---
title: "Machine Check Errors on M1730"
date: 2009-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wiresquire on 2009-02-17
Hi

I have an M1730 with T7700 Core Duo, dual 8700M GTs and BIOS rev A09. I'm running 8.04 x86_64(with all updates).

I have noticed that when I am running games I get "Machine check events logged" in /var/log/messages (or via dmesg). I installed mcelog to try and get some more information. It reports:
```
MCE 0
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
CPU 0 THERMAL EVENT TSC 83ff31e085c
Processor core below trip temperature. Throttling disabled
STATUS 881b00c0 MCGSTATUS 0
MCE 1
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
CPU 1 THERMAL EVENT TSC 83ff31e3544
Processor core below trip temperature. Throttling disabled
STATUS 881603c0 MCGSTATUS 0
```
The temperatures for CPU seem to be within limits. Normal operation is ~40-50C. When gaming it seems to be mostly around 65-75C, occasionally going up to high 70s for a very short time. The fan comes on OK, but it never goes full blast. The machine seems to operate fine even though the errors occur, ie no freezing or noticeable performance or other glitches.

I tried running a CPU stress test (stress -c 13). This gets both cores running to 100%. The fan comes on in low(?), continues to run during the test, and almost immediately stabilises the temperature at 70C. Eventually, the error pops up.

There's not a lot of info I could find/understand about this specific error. Can anyone explain what these errors really mean, and whether I should be worried ?

TIA
ws

PS: The graphics card temperatures seem fine. When gaming they are around 60-67C. I get the errors with 177.82 and 180.29 drivers. As the error is specifically about the CPU, and I can reproduce it with CPU only stress test, I guess anything GPU is pretty irrelevant...

---

### Post by wiresquire on 2009-02-25
Seeing as there's been no response here, could a mod move this into the Hardware & Laptop forum?

TIA
ws

---

### Post by wiresquire on 2009-11-27
Just in case anyone else ever sees this error message, I have since upgraded to 9.04 and have *never* seen this message.

I put it down to kernel errors in 8.04.

ws

---

