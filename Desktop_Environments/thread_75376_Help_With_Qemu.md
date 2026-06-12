---
title: "Help With Qemu"
date: 2005-10-13
forum: Desktop Environments
---

### Post by rozojc on 2005-10-13
Hi every1. I have been (unsuccessfully) trying to install Qemu with the Kquemu module on my system.

I am following the instructions found on [http://ubuntuforums.org/showthread.php?t=39513]("http://ubuntuforums.org/showthread.php?t=39513")
but I get a lot of errors...

I downloades the latest kernel image and kernel headers via Synaptic.
uname -r gives me : 2.6.12-9-386
I changed that in the configuration file as the instructions said, got the packages I needed, but as soon as I run "make" I start getting errors like:

dyngen.c: In function ‘load_object’:
dyngen.c:508: warning: pointer targets in assignment differ in signedness

Specially a lot that say things like "pointer targets in assignment differ" blah blah blah...

After some time and a lot of output including those mistakes it says:
[html]<textarea>

/home/rozojc/temp/temp/qemu-0.7.2/target-i386/ops_sse.h:574: error: unable to find a register to spill in class ‘GENERAL_REGS’
/home/rozojc/temp/temp/qemu-0.7.2/target-i386/ops_sse.h:574: error: this is the insn:
(insn:HI 18 17 19 0 /home/rozojc/temp/temp/qemu-0.7.2/target-i386/ops_sse.h:569 (set (strict_low_part (subreg:HI (reg/v:DI 63 [ r ]) 0))
        (mem/s/j:HI (plus:SI (mult:SI (reg:SI 64)
                    (const_int 2 [0x2]))
(reg/v/f:SI 59 [ s ])) [0 <variable>._w S2 A16])) 52 {*movstricthi_1} (insn_list:REG_DEP_TRUE 16 (insn_list:REG_DEP_TRUE 12 (insn_list:REG_DEP_TRUE 53 (nil))))
    (expr_list:REG_DEAD (reg:SI 64)
        (nil)))
/home/rozojc/temp/temp/qemu-0.7.2/target-i386/ops_sse.h:574: confused by earlier errors, bailing out
make[1]: *** [op.o] Error 1
make[1]: Leaving directory `/home/rozojc/temp/temp/qemu-0.7.2/i386-user'
make: *** [all] Error 1
</textarea>[/html]

Any ideas? I know I can run qemu by installing the .deb file but I want to run it with the kqemu module in order for it to run faster...

What am I missing?

---

### Post by ayates on 2005-10-13
Which version of the compiler are you using ?
I think it needs 3.3 or 3.4.

---

### Post by rozojc on 2005-10-13
Solved! Yes, it needed 3.3! thanks Note: 3.4 does not work

---

### Post by rozojc on 2005-10-13
Something weird is happening now... The first time I ran it Windows inside qemu detected my processor as bein 1.6ghz, but now it always says its 800mhz....

any ideas?

---

