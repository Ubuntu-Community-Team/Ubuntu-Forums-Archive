---
title: "force feedback in 8.10"
date: 2008-11-30
forum: Gaming &amp; Leisure
---

### Post by tgpraveen on 2008-11-30
so i am gonna buy a cheap usb gamepad with force feedback support and i want to know will the force feedback support work in ubuntu 8.10? anyone tried it?
which games have support for it natively in ubuntu?
with wine games what will happen?

 if it helps i know that the force feedback support works in windows only after installing drivers that comes along with the gamepad in a cd.

---

### Post by holmes0 on 2008-12-02
Unfortunately, getting force feedback in Linux is not straightforward. My experience in 8.04 (but it should be the same with 8.10) is the following one:
- force feedback can work if the kernel is compiled with the correct option (HID_FF if I remember right),
- FF is disabled by default in 8.04 and probably in 8.10 as weell. You have to compile your own kernel,
- Suppose that you managed to compile your kernel, only a few game pads are supported (mainly Logitech joystick and wheels),
- As for the games, VDRIFT supports FF (but it is not perfect according to what I read in the forum), BZFlag has a minor support, Freespace does not support FF,
- Apparently, one of the problem with FF programming with Linux is the absence of FF support in the SDL library. Work is being done (?), but it does not work so far,
- Concerning Wine, I have no experience. Some information is given in the Wine HQ site. BZFlag should work.

Good luck !

---

### Post by tgpraveen on 2008-12-02
> **holmes0 said:**
> Unfortunately, getting force feedback in Linux is not straightforward. My experience in 8.04 (but it should be the same with 8.10) is the following one:
- force feedback can work if the kernel is compiled with the correct option (HID_FF if I remember right),
- FF is disabled by default in 8.04 and probably in 8.10 as weell. You have to compile your own kernel,


Good luck !
why is it disabled by default? any specific reason or just the general stupidity?

also is kernel recompilation easy? will it ruin my auto update system?

thx for ur reply.

---

### Post by holmes0 on 2008-12-03
FF support seems to be disabled in most (if not all) Linux distros. One reason for this is probably the limited number of  games supporting it. Some progress can be expected in the future. I read in the Freespace forum that devs were ready to reimplement FF as soon as it is supported in the SDL library.

If you want Ubuntu to support FF by default, you should write to the Ubuntu kernel team.

Concerning kernel compiling, I tried it with 8.04 and managed to compile a FF-enabled kernel. However, for reasons not clear to me, I did not have any more sound and wifi.
There was a more serious problem however. My joystick is a Microsoft SideWinder FF 2 (USB). The support for this particular joystick in the 2.6.25 kernel documentation is claimed to be experimental. And this is true! I tested FF effects with a software (I don't remember the name) whose role is to generate effects of you choice (rumble, move on the right, sine motion, ...). The first effect was good (so I could check that FF worked) but I always had a system freeze at the second test.
Things could have changed with 8.10 (kernel 2.6.27) but so far I did not find the time and courage to test it.
Note that once you have compiled the kernel, you can choose whichever one you want to use at system boot. I don't think the update system will be influenced by kernel (but I am not sure of this). Another thing, if you use a custom kernel and report a problem with a software (any one), you won't get any help from the community because the problem could come from your custom kernel. You would have to reproduce the problem with a regular kernel (which is not a problem since you can choose your kernel at boot).

Good luck !

---

### Post by holmes0 on 2009-07-23
Hi,

Since 9.04 (and kernel 2.6.28, it is no longer necessary to compile a custom kernel. Force Feeback support is from now on a standard feature. I have personnaly tested it with a Sidewinder Force Feedback 2 using ff-utils and gforce (a ff testing application with a GUI). It works perfectly. It appears Sidewinder support is no longer experimental since I don't have any more freeze as it used to happen with previous kernels.

Now we have to wait for the next SDL 2 (with a FF API) which is now the single element lacking for a FF support within Freespace SCP!

Hope it will come soon ...

---

### Post by Drahcir on 2009-07-23
I brought one of [these](http://www.b2c-support.com/pc-usb-doubledual-shock-joypad-gamepad-game-controller-p-194.html) at the beginning of the year. Cheap from China, but it is working fine.

There's a kernel driver for it which made it into release 2.6.30.

---

