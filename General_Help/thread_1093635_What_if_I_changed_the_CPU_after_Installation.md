---
title: "What if I changed the CPU after Installation?"
date: 2009-03-11
forum: General Help
---

### Post by UranUtan on 2009-03-11
Hi,

On a working Ubuntu 8.10 x64. What would happen if I changed the CPU?

Case 1: (Same CPU micro architecture) Change from Intel Core 2 Duo to Core 2 Quad cores.

Case 2: (different CPU) Change from an Intel CPU to AMD Phenom X4.

Would Ubuntu boot normally or would it hang? In case of failure to boot what is the appropriate way to fix the issue? Assuming the other hardware parts are unchanged.

Thanks in advance for any help.

---

### Post by rbmorse on 2009-03-11
Unlike Windows, Ubuntu will check the hardware configuration ever time it boots and load the appropriate drivers as long as they are available. In the cases you cited, Ubuntu should boot as if nothing has changed, except to take advantage of any capabilities the new hardware brings to the fight.

---

### Post by MaxIBoy on 2009-03-11
As long as you're not trying to run a 64-bit OS on a 32-bit CPU, and you use the same architecture (in other words, you don't go from x86 to SPARC or from MIPS to PPC,) it will run just fine.

---

### Post by UranUtan on 2009-03-11
Cool, that makes the job simpler. To make the scenario a little bit more complicate.

A CPU change may require a change of motherboard, which may have different chipset for integrated video, audio, network, etc.

I assume Ubuntu will try to accommodate automatically the new devices. Let's assume that Ubuntu has troubles to recognize the video device. Am I right in assuming that it will just fallback to a basic video mode. Then all I need is to find the video driver and reconfigure Xorg ?

More exactly, I am worried about something goes wrong and Ubuntu can no longer boot. Could such a severe issue be possible?

NOTE: this is a modest home computer upgrade, there is no drasctic change like intel x32 to SPARC or IDE to RAID controller.

---

### Post by rbmorse on 2009-03-11
I don't think you'll have a fatal error...if you go from an ATI GPU to an nVidia GPU (or vice versa) you might end up is some reduced video mode until you get things straightened out.  If nothing else you can boot from the LiveCD and work on the system from there.

---

### Post by lindsay7 on 2009-03-11
Another good reason to go Ubunto. I changed out an amd64 dual core to a faster amd64 dual core on my windowsVista machine. The penalty was the media player would no longer function. After long calls to MS the result was, buy 7 when it comes out. That machine is now 100% Ubuntu.

---

### Post by UranUtan on 2009-03-12
> **rbmorse said:**
> Unlike Windows, Ubuntu will check the hardware configuration ever time it boots and load the appropriate drivers as long as they are available.

I don't know if it's a good design. What if I have already tuned the hardware setting and suddenly Ubuntu decides to override it?

Now I understand why all my graphics resolution settings are always reverted back to an arbitrary state. I have two computers with different graphics chip. Every time I set the right graphic mode (resolution & frequency) either by using the NVidia applet or by just cliking repeatedly the "Detect Monitor" in the "Screen Resolution" Admin Option. After reboot, I always end up with a poorer graphic capacity.

So I would day that the hardware auto configuration feature is not always good. May be this should be invoked on demand. In my case with the graphics issue above, the auto configuration drove me nuts but I didn't know why.

---

### Post by fjgaude on 2009-03-12
I've gone from an AMD dual-core motherboard to and Intel one using the same boot drive and raid array without a hitch. Ubuntu rules. I did use the same graphic card from old md to new.

---

### Post by UranUtan on 2009-03-12
> **fjgaude said:**
> I've gone from an AMD dual-core motherboard to and Intel one using the same boot drive and raid array without a hitch. Ubuntu rules. I did use the same graphic card from old md to new.

Oh super, I'm curious, Which RAID do you use? FakeRaid or MDAdm? Which RAID controler? On board or dedicated RAID controler?

---

### Post by fjgaude on 2009-03-13
I've used **mdadm** for the last three years without issue, except to learn how to use it under all situations... lots to understand.

The four drives are SATA working off a Gigabyte MB, which has eight ports.

I've used **dmraid**, fakeRAID yeats ago but decided it wasn't for me.

I use three levels of backup as the raid5 only protects against a drive failure, not other things. My work is important. <smile>

---

