---
title: "General slugginesh of Unity/Compiz, Ubuntu 11.10"
date: 2011-11-24
forum: Desktop Environments
---

### Post by typhoon_tip on 2011-11-24
Just share an experience (marked as SOLVED already...) that may be helpful to somebody else as well, as it is a problem often lamented by many people.

I have a ThinkPad T400 laptop with ATI Radeon HD 3400 video card. After tweaking compiz and installed the proprietary FGLRX drivers from AMD website, everything is fine, but still, after running for a while (few hours) there was random slowing down and other moments where the frame rate dropped down considerably.

I just bumped into a thinkwiki page for my laptop, and discovered that Lenovo provide a bootable CD iso for BIOS update. Noticed that my version was quite old too, so I did an update. Well, believe it or not, all the slowness has gone. It is smooth as silk now and smoothness remain stable, even by opening up a lot of programs.

Talk about dumb luck sometimes, it really looks like they may have improved I/O handling in my case, and with the newest Kernel I can take advantage of the full acceleration. Moreover, temperature of GPU and CPU stay much lower now than before (fan speed stay lower too).

**ATTENTION: I am not saying that everyone should update their system's BIOS, it is a very dangerous and risky operation if you are not skilled, so don't do it. If something go wrong, you are not able to boot your computer anymore.**

---

