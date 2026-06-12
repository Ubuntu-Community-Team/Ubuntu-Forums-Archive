---
title: "smp or no smp"
date: 2006-07-16
forum: Desktop Environments
---

### Post by dksdk on 2006-07-16
ok, i have searched a lot and have'nt had clear picture.
Looked at this thread as well. [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
i am on dapper on my vaio with  mobile P4, which is HT enabled.
cpu info
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz
stepping        : 9
cpu MHz         : 3057.179
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 3192.71

uname -a
Linux ubuntumaruti 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686 GNU/Linux

my question is does this mean smp is enabled. then why does it not say 2.6.15-26-686-smp OR smp preempt means 686 comes packaged with smp.
if yes why my dmesg says

[17179570.128000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179570.128000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179570.128000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179570.128000] CPU: L2 cache: 512K
[17179570.128000] [COLOR="DarkOrange"]CPU: Hyper-Threading is disabled[/COLOR]
[17179570.128000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[17179570.128000] mtrr: v2.0 (20020519)
[17179570.128000] Enabling fast FPU save and restore... done.
[17179570.128000] Enabling unmasked SIMD FPU exception support... done.
[17179570.128000] Checking 'hlt' instruction... OK.
[17179570.144000] SMP alternatives: switching to UP code
[17179570.144000] checking if image is initramfs... it is
[17179570.580000] Freeing initrd memory: 6809k freed
[17179570.596000] ACPI: Looking for DSDT ... not found!
[17179570.596000] ACPI: setting ELCR to 0200 (from 0c00)
[17179570.624000] CPU0: Intel Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz stepping 09
[17179570.624000] SMP motherboard not detected.
[17179570.624000] Local APIC not detected. Using dummy APIC emulation.
[17179570.624000] Brought up 1 CPUs

i installed linux-686-smp, but i did'nt get any 686-smp kernel at boot.

i am totally confused about this.
any clarifications wellcome. pl tell if i have smp enabled if not how to enable it.
thanks in advance.

---

### Post by Jagot on 2006-07-16
Go to the System Monitor.  It's under either Prferences or Administration but I'm not at my Ubuntu box and can't remeber.  Can't remember equally if it's the default tab or the next one that is the one you need, but one of them displays the activity of the processors - if it says you have 2 processors then it is enabled.

I have the SMP kernel and it won't label itself as 686-smp in GRUB.

---

### Post by dksdk on 2006-07-16
sorry i forgot to mention this. i did check in the system monitor, under resources. it displays only one cpu. thank you for the reply.

---

### Post by Jagot on 2006-07-16
Providing HT is actually enabled in your BIOS, providing you've installed it correctly it should work.  You could always try again just to ensure it is installed:

```
sudo aptitude update && sudo aptitude install linux-686-smp
```

---

### Post by dksdk on 2006-07-16
> **Jagot said:**
> Providing HT is actually enabled in your BIOS, providing you've installed it correctly it should work.  You could always try again just to ensure it is installed:

```
sudo aptitude update && sudo aptitude install linux-686-smp
```
thank you i tried &
sudo apt-get install linux-686-smp
Reading package lists... Done
Building dependency tree... Done
linux-686-smp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

i did'nt get any mention of cpu, processor or HT in the bios.
under what section is it?
could you pl tell me how to check and enable it in bios.

---

### Post by Jagot on 2006-07-16
I'm afraid I'm not at a computer where I can access the BIOS so I can't guide you through it.  There generally aren't too many sections to look through though, so have a browse and it will be there.  When you find it it will enable you to enable/disable it - you should just need to press a key - it will tell you which one.  Then save and exit the BIOS and restart.

---

### Post by dksdk on 2006-07-16
right, i had a detailed look at the bios and i could'nt find any option to enable HT. Actually there is no mention of HT in the bios. so does this mean
 -HT i not available for this CPU. or 
-HT rendering is not available at bios level.

---

### Post by autocrosser on 2006-07-16
You also need to modify your /etc/grub/menu.lst by adding in your kernel area:
kernel        /boot/vmlinuz-2.6.15-26-686 root=/dev/hdb1 ro quiet splash ht=on <---- add the "ht=on"

I checked with dmesg & went from "CPU--Hyper-Threading disabled"
to a seperate loading for each CPU--seems to have made a good increase in speed in my system (Pent D 805 (2.66ghz) with 3g ram)

Dmesg reports:
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2795.714 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.524000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.524000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.952000] Memory: 3104964k/3145408k available (2110k kernel code, 39124k reserved, 595k data, 332k init, 2227904k highmem)
[17179570.952000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.032000] Calibrating delay using timer specific routine.. 5599.74 BogoMIPS (lpj=11199490)
[17179571.032000] Security Framework v1.0.0 initialized
[17179571.032000] SELinux:  Disabled at boot.
[17179571.032000] Mount-cache hash table entries: 512
[17179571.032000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179571.032000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179571.032000] monitor/mwait feature present.
[17179571.032000] using mwait in idle threads.
[17179571.032000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.032000] CPU: L2 cache: 1024K
[17179571.032000] CPU: Physical Processor ID: 0
[17179571.032000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000651d 00000000 00000001
[17179571.032000] mtrr: v2.0 (20020519)
[17179571.032000] Enabling fast FPU save and restore... done.
[17179571.032000] Enabling unmasked SIMD FPU exception support... done.
[17179571.032000] Checking 'hlt' instruction... OK.
[17179571.048000] SMP alternatives: switching to UP code
[17179571.048000] checking if image is initramfs... it is
[17179572.164000] Freeing initrd memory: 6820k freed
[17179572.176000] ACPI: Looking for DSDT ... not found!
[17179572.192000] CPU0: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[17179572.192000] SMP alternatives: switching to SMP code <-----!!!!!!!!
[17179572.192000] Booting processor 1/1 eip 3000
[17179572.204000] Initializing CPU#1
[17179572.284000] Calibrating delay using timer specific routine.. 5590.41 BogoMIPS (lpj=11180824)
[17179572.284000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179572.284000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179572.284000] monitor/mwait feature present.
[17179572.284000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.284000] CPU: L2 cache: 1024K
[17179572.284000] CPU: Physical Processor ID: 0
[17179572.284000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000651d 00000000 00000001
[17179572.284000] CPU1: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[17179572.284000] Total of 2 processors activated (11190.15 BogoMIPS).
[17179572.284000] ENABLING IO-APIC IRQs
[17179572.284000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.956000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179572.956000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179572.956000] ...trying to set up timer as Virtual Wire IRQ... works.
[17179573.104000] checking TSC synchronization across 2 CPUs: passed.
[17179573.108000] Brought up 2 CPUs

;)8)

---

### Post by Dubbayoo on 2006-07-16
> **autocrosser said:**
> You also need to modify your /etc/grub/menu.lst by adding in your kernel area:
kernel        /boot/vmlinuz-2.6.15-26-686 root=/dev/hdb1 ro quiet splash ht=on <---- add the "ht=on"


;)8)


I don't believe thats correct. I don't have that on my dual Xeon HT-enabled system and here is my System Monitor. I didn't do anything other than install the 686 kernel.

[IMG]http://www.dubbayoo.net/files/pics/screenshots/ubuntu-mem-usage.jpg[/IMG]

---

### Post by Dadgumit on 2006-07-16
FWIW, I have recently had problems getting SMP functional. I DID get it functional by enabling ACPI APIC support in my BIOS.

However, it has caused more problems than it has fixed (described here: [http://www.ubuntuforums.org/showthread.php?t=217066)](http://www.ubuntuforums.org/showthread.php?t=217066)). Also, I am on an AMD CPU and do not know if the setting I changed is proc/mobo specific. 

Hope that helps in any regard. Good luck!

---

### Post by Thund3rstruck on 2006-07-16
I'm confused about this as well. My system monitor shows 2 cpus on my dual core acer laptop but dmesg tells me that hyperthreading is disabled?? How do I enable it if its disabled?

```

[17179569.904000] Initializing CPU#1
[17179569.984000] Calibrating delay using timer specific routine.. 3333.81 BogoMIPS (lpj=6667633)
[17179569.984000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000
00000000 0000c1a9 00000000 00000000
[17179569.984000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.984000] monitor/mwait feature present.
[17179569.984000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.984000] CPU: L2 cache: 2048K
**[17179569.984000] CPU: Hyper-Threading is disabled**
[17179569.984000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000040 0000c1a9 00000000 00000000
[17179569.984000] CPU1: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[17179569.984000] Total of 2 processors activated (6671.50 BogoMIPS).

```

---

### Post by autocrosser on 2006-07-16
Hi Dubbayoo--

There is a difference between SMP & Hyper-threading--I showed two cpus in my system monitor before I enabled Hyper-Threading. Acording to Intel, you will get more performance with Hyper-Thread enabled & you must
#1--enable it in your Bios
#2--make sure that you enable it in your kernel

Note: the app you are using must be Hyper-Thread aware to take advantage of the speed boost--My normal bench-mark app is Seti@home--Very processor-aware & cpu-intensive--I've seen times to complete one work-unit come down on the average 2/4 hours after H/T--This is using the same Seti-Enhanced app & averaged over 30 work-units.

This is a major processor boost as far as I am concerned--So I posted the simple way to made use of it for those that can--"most" newer Intel cpus are H/T-able--take a look at your processor specs & enable it!!

---

### Post by dksdk on 2006-07-17
hi again. thanks autocrosser. so i changed my menu.lst and added ht=on like this
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda4 ro resume=/dev/hda8 nolapic noapic quiet splash ht=on vga=792
but i still see only one cpu in my system monitor.
any more tricks!
can anyone tell me how to activate it in bios. i cant find any entry for this in bios. thank you.

---

### Post by dksdk on 2006-07-17
ok. after googling a lot i have come to this conclusion.
I have P4 which supports HT. But the bios does'nt support HT. whom to blame.
 sony web site says i can update my phoenix bios to version R0110X1, which i already have. But this does'nt support HT. 
So why to have HT in the first place when you cant use it.

It is like you have a fast car, but the roads are crappy. so you cant go beyond 40, can you.;)

---

### Post by autocrosser on 2006-07-17
Yes--H/T is a matter of both the processor & the motherboard--It's like a hotrod engine bolted into a otherwise stock VW Bug, wants to go fast--but has it's limits.

---

