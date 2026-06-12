---
title: "Ubuntu still uses default radeon driver when amdgpu is installed"
date: 2019-02-20
forum: Gaming &amp; Leisure
---

### Post by regulator2 on 2019-02-20
Hi guys
for the best GPU driver everyone is using this "Padoka PPA" however once you install it there is no easy way to tell Ubuntu to use that driver.. I had to follow these instructions found in a backwater system involving modifying the GRUB, Xorg and then blacklisting the default driver..

I can imagine a lot of people are going to get stuck on this issue.. Ideally there would be a setting in Ubuntu to switch the driver used?

these are the instructions:
[https://github.com/redmcg/wine/issues/5](https://github.com/redmcg/wine/issues/5)

---

### Post by QIII on 2019-02-20
"Best"? "Everyone"?

AMDGPU installed for me and is working fine.  Are you sure it is using the Radeon driver?  How have you determined this?

If your GPU is supported, the AMDGPU module is loaded.  If not, the Radeon module is loaded.  The fact that they are both present and available does not mean that the Radeon driver is being used.  

On my machine

```
lsmod | grep radeon
``` returns nothing, which means that the Radeon module is not loaded and running, despite the fact that it is available in the kernel.

```
lsmod | grep amdgpu
```

returns

```
amdgpu               3166208  39
amdchash               16384  1 amdgpu
amd_sched              24576  1 amdgpu
amdttm                110592  1 amdgpu
amdkcl                 28672  4 amdkfd,amd_sched,amdttm,amdgpu
drm_kms_helper        172032  1 amdgpu
drm                   401408  15 drm_kms_helper,amd_sched,amdttm,amdgpu,amdkcl
i2c_algo_bit           16384  2 igb,amdgpu

```

which means that the AMDGPU module is loaded and running.

From your link:
> After some research, I found a solution to the problem. By default, Ubuntu still use the Radeon driver and not AMDGPU.

This is absolutely not true.  In fact, AMD works specifically with Canonical and develops the AMDGPU driver ***on Ubuntu.***  

```
lspci -k | grep -EA3 'VGA|3D|Display'
```

returns

```
47:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tonga XT / Amethyst XT [Radeon R9 380X / R9 M295X] (rev f1)
        Subsystem: PC Partner Limited / Sapphire Technology Radeon R9 380X Nitro 4G D5
        Kernel driver in use: amdgpu
        Kernel modules: amdgpu

```

The R9 380X is supported by AMDGPU.  The GPU used by the quoted user in your link is not.  THAT is the problem.  AMDGPU does not support his/her GPU (the hardware technology can't use it).  Thus, the Radeon module is loaded.  The same goes for the OP of the thread.  

Radeon is certainly not used by default if the hardware is supported by AMDGPU.

What GPU is in your machine?  Is it a dual GPU system (as in a laptop)?  Are both GPUs supported by AMDGPU?

Is your system one with an APU?  What is the GPU?

Fair warning about PPAs and video drivers:  They screw up regular updates and have caused serious problems with updating to newer releases of Ubuntu or point releases with HWE updates.

---

### Post by regulator2 on 2019-02-20
Hi QIII thanks for the quick reply..

I determined which driver was in use by typing lspci -k | grep -EA3 'VGA|3D|Display'

If i search hard enough I can find an official steam play instructions post telling people they should use this driver (padoka)

I have an Radeon R280X.. I have just discovered on the Ubuntu About page the OS thinks I have a Radeon hd 7900 series??

I have one of those i5 CPUs with built in graphics which might have caused some confusion.. and the fact that when I installed Ubuntu it did the install offline ?

anyways appreciate your help

---

### Post by QIII on 2019-02-20
Do you have a hybrid system with an Intel CPU/GPU integrated and an AMD GPU dedicated on a laptop?

If so, that is your problem.  The OEMs have not left Linux users with a workable situation.

If not and your machine is a desktop, then you will need to blacklist the Intel GPU in your BIOS/EFI to make sure that the AMD GPU is used.  But that may still not work.  Your GPU is GCN 1.0.  I don't know if AMD has worked back to GCN 1.0, but on release AMDGPU worked only with GCN 1.1 and later hardware.

---

### Post by regulator2 on 2019-02-20
Yeah, A desktop with built in intel graphics but running through PCIE Radeon card. does the integrated video need to be disabled in the BIOS when setting up ubuntu?

also any thoughts on why Ubuntu thinks I have a 7900?

---

### Post by QIII on 2019-02-20
Probably because it is a "souped up" Tahiti chip based on an HD 7000 series GPU.

If it's GCN 1.0, it is not likely supported by AMDGPU.

The integrated GPU would need to be blacklisted in the BIOS prior to installing the OS for the best results.

I'm not sure how much you may have muddied the waters for yourself with the PPA.

---

### Post by regulator2 on 2019-02-20
Yep a quick google and its a souped up 7900.. also GCN 1.0.

had a quick read about "GCN" its basically support for Vulkan etc?

Might need a separate thread but if I purchased a newer Radeon RX 480 can I just drop it in or do I need to remove and reinstall drivers?

---

### Post by QIII on 2019-02-20
Graphics Core Next (GCN) is a new hardware architecture that replaced AMD's older hardware.

If it weren't for the fact that you mentioned Steam, I'd say just use the older hardware with Radeon and be happy.  It works pretty well.

If you are interested in Steam, then you will have to go with a GCN 1.1 card or later and use AMDGPU (I also have the proprietary AMDGPU-Pro overlay installed for some things I do).  But as with all things Linux, don't buy the absolute newest stuff or you will run out from under driver support until it catches up.

Despite the fact that AMD is a member of the Linux Foundation and a long-time kissing cousin with Canonical, they still know which side their bread is buttered on -- and that's Microsoft.  But as a ratio of resource expenditure/market share, the scale is definitely tipped towards Linux.  AMD spends enough resources on Linux that their bean-counters must cringe.

---

### Post by regulator2 on 2019-02-24
thanks for your help mate, I got a RX 570 second hand and will look at switching drivers

---

