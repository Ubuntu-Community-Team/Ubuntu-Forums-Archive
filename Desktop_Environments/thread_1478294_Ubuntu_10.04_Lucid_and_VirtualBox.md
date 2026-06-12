---
title: "Ubuntu 10.04 Lucid and VirtualBox"
date: 2010-05-09
forum: Desktop Environments
---

### Post by Manoboy on 2010-05-09
I installed the 10.04 64 bits and then VirtualBox 64 (version Ubuntu 9.10 ("Karmic Koala") AMD64).
When I create the VM it does not give me an option if I want to install an OS 32 or 64 bits, eg do not offer Ubuntu option 32 or 64.
Well keep the configuration and boot the machine.
I am wanting to install .iso Karmic that I made before installing the Lucid in my note. The Karmic wal also 64-bit.
When the installation begins msg appears:

This kernel requires an x86-64 CPU, But only detected an i686 CPU.
Unable to boot - please use Appropriate kernel for you CPU.

Anyone know solution to this problem?

---

### Post by Pablo Pablovski on 2010-05-09
I believe it's not possible to run 64bit virtual machines inside a 64bit host, unless you have a BIOS / CPU capable of hardware virtualisation. 

If your CPU doesn't support hardware virtualisation, you should be able to install and run the 32bit version in a VM. It have a similar installation and it works well.

More here:
[http://forums.virtualbox.org/viewtopic.php?f=1&t=19420]("http://forums.virtualbox.org/viewtopic.php?f=1&t=19420")

---

### Post by tgm4883 on 2010-05-09
When selecting the OS type that you are trying to install, you should be able to select Ubuntu or Ubuntu 64-bit. (this is in the second os box)

---

### Post by Manoboy on 2010-05-10
> **tgm4883 said:**
> When selecting the OS type that you are trying to install, you should be able to select Ubuntu or Ubuntu 64-bit. (this is in the second os box)

Well then, this option does not appear to me.
Is there any solution for this?

---

### Post by tgm4883 on 2010-05-10
> **Manoboy said:**
> Well then, this option does not appear to me.
Is there any solution for this?

It's possible your CPU doesn't support VT extensions. What CPU do you have?

---

### Post by Manoboy on 2010-05-10
There is no such option in the BIOS of my notebook.

Acer Aspire 5920 
Core 2 Duo T5450 1.66 Ghz

---

### Post by 3rdalbum on 2010-05-10
> **Manoboy said:**
> There is no such option in the BIOS of my notebook.

Acer Aspire 5920 
Core 2 Duo T5450 1.66 Ghz

Intel says this CPU doesn't have virtualisation features. You're limited to running 32-bit guest operating systems unfortunately.

---

### Post by Manoboy on 2010-05-12
3rdalbum,

Thanks for the reply.

---

### Post by wgates on 2010-05-21
I had this problem after I upgraded from Virtualbox 3.0 to 3.2. I fixed it by removing KVM.

---

