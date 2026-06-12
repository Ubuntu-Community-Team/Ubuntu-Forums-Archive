---
title: "Ubuntu crashes when plugging in a USB device"
date: 2006-07-01
forum: Desktop Environments
---

### Post by DktrKranz on 2006-07-01
Hello,
I noticed a strange behaviour when plugging in a USB device in Dapper. As soon as I plug in any device, system freezes completely beyond any recovery.
Initially I thought this problem was originated by my Bluetooth dongle but yesterday a friend of mine brought me his USB pendrive and the system crashed :cry:
I use a 2.6.16 patched kernel, the same used in Breezy without any problem. I tried to use the default kernel (2.6.15-xxx) with the same result. Even LiveCD crashes!
Any suggestion? Thanks

---

### Post by DktrKranz on 2006-07-01
It seems this problem affects hal subsystem.
I tried to disable dbus and hal services and system didn't crash.

---

### Post by minze on 2006-07-02
Hi,

I just installed 6.06 on the PC of my mother, it was runnin 5.04 before without any trouble. But now it has the same issue as the one you describe after inserting her benq digital camera...
So you are not alone, maybe a bugreport should be filed ? 
(oh here  HP 7760 USB printer did work fine though)

Greetz,
Minze

PS : try pluging in the usb stick before booting. that DID work ... just istn't very convenient

---

### Post by DktrKranz on 2006-07-02
On my friend's PC everything is Ok, so this bug should be hardware-dependant.
Could you make this test? Try to playback an audio file before plugging in the device. What happens?

[QUOTE=minze]PS : try pluging in the usb stick before booting. that DID work ... just istn't very convenient[/QUOTE]
I already noticed this, so it is definitely not a USB bug. Another solution I've found is disabling dbus before plugging in any device. You can freely mount or use the device, but once you restart that service a crash occours. Really weird.

---

### Post by minze on 2006-07-02
Hmm too bad I'm allready back home atm. I could try this evening.

also I did a lspci & cat /proc/cpuinfo. So that's all I have elas...

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:00:0f.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)
```

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 3
cpu MHz         : 800.191
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1602.93
```


Also mouse & keyboard are on USB , and they are laggy when the HDD is accessed... but that could be another issue. But first this one ;)

Minze

---

### Post by DktrKranz on 2006-07-03
I ran a couple of tests in order to get a kernel oops but it seems no one is generated.
I'm going to send a bug report, maybe we'll be able to get rid of this weird bug.

---

### Post by minze on 2006-07-03
Could you post the bugzilla id/number/whatever ;)

If I can add info I shall

---

### Post by DktrKranz on 2006-07-03
Voilà: [https://launchpad.net/distros/ubuntu/+source/hal/+bug/51771](https://launchpad.net/distros/ubuntu/+source/hal/+bug/51771)
I noticed I repeated the post twice, will it take more visibility? Sorry for that.

---

### Post by minze on 2006-07-03
Just noticed when looking at the report, both our troubled machines are older ones using the same usb chipset. 

Still, it shouldn't matter. 

And I just had a call telling me that indeed other usb devices cause the same crash

:(

---

### Post by rattlerviper on 2006-07-03
On my machine (just updated to dapper last night) i can plug and unplug usb items and it doesn't cause any problems. Hope you can figure what's wrong. For what it's worth windows xp used to do that to me after i installed service pack 2, so so it's not just a open scource problem with thing like this slipping through.  The difference is I believe it will get fixed here, Microsoft never made it work on my machine again.

---

### Post by DktrKranz on 2006-07-04
I'm curious to see if Kubuntu is affected too. I'm going to download and test it in LiveCD mode since Ubuntu crashes in both methods. It could be useful in order to trace down the whole thing.

---

### Post by DktrKranz on 2006-07-04
Latest update: Kubuntu is affected too :cry:

---

### Post by DktrKranz on 2006-07-07
It seems this bug is related to uhci_hdc kernel module. If you remove it using *rmmod* a crash doesn't occour.
Please, let me know if you see the same result.

---

### Post by DktrKranz on 2006-07-20
Maybe we're close to a solution. I tried to pass *acpi=force* option to the bootloader and no more crashes :D
I tried this with the LiveCD, I'm going to test it on a hdd-installed version as soon as possible.
Please, verify it on your machines.

---

