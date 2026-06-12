---
title: "Recompiling my kernel, tips on config?"
date: 2009-08-13
forum: Desktop Environments
---

### Post by oOarthurOo on 2009-08-13
I'm recompiling my Jaunty kernel to enable the PHC patch so that I can undervolt my laptop. Some of the other things I'm want to do while in there are the following:

1. Optimize for my processor. A intel duo core. Which I believe means changing the processor type from Pentium Pro to Pentium M.

2. Under kernel hacks, disable debugging. I understand this will result in a smaller kernel.

3. Change preemption model to 'Voluntary Kernel (desktop) 

4. Disable dell and Toshiba workarounds

5. Turned off high memory support.

6. Change timer frequency to 1000mhz

7. Disable bluetooth & amateur radio

8. Remove un-needed drivers

9. Compile acpi as a module, so that I can update PHC later without having to recompile.

10. Change the default cpu governor to ondemand, which will later allow me to remove all cpu userspace tools, since it's the only governor I use

Any other tips thoughts on this? I know I can optimize the build for duo core, but is there anything else in the kernel config I ought to do?

Many thanks for any tips.

---

### Post by lensman3 on 2009-08-13
The current kernel config file is for the running kernel is found in /boot.  Copy and rename to .config in  the kernel install directory and go from there. Turn off and on the modules  you want.  That starting .config file is from a working kernel.  It is a lot easier to use this than to remember what needs turned on and off.

---

### Post by oOarthurOo on 2009-08-15
It's a good point lensman. I had planned on doing that but thanks for mentioning it anyway.

---

