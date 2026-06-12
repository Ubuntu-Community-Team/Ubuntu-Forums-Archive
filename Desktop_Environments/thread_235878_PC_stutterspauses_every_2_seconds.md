---
title: "PC stutters/pauses every 2 seconds"
date: 2006-08-13
forum: Desktop Environments
---

### Post by i_know_tim on 2006-08-13
My ubuntu system is stuttering constantly. The whole system locks up for a fraction of a second every couple of seconds. The system is keeping time correctly. Dmesg doesn't appear to give up any clues. I am at a loss as to what to try next. I am using the 2.6.15-26-686 kernel and also tried the 386 kernel. Currently I have done the following to try to fix the problem(Note i am a noob):

```
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro quiet splash acpi=off
```
I have loaded the legacy nvidia driver
tried Xubuntu by doing a apt-get install xubuntu-desktop and logging into an xfce session.

Does anyone know what I should try or what I should look at?

Thanks for any assistance in advance

---

### Post by i_know_tim on 2006-08-14
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:0f.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
0000:00:10.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
```

I thought I would post this for a little more information especially as it shows the ACPI. It is a PIII 733 with 256MB of ram. Anyone else having problems with ubuntu on this chipset? ](*,) < so appropriate After reading about other people with similar issues and ACPI being the cause I am pretty sure it is something to do with ACPI but I am not really sure how to prove or test it.

---

### Post by i_know_tim on 2006-08-16
OK I have fixed the stuttering. First I tried what was in this thread but it did not work. Can anyone tell me if this is correct for setting up apm? [http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264). What did work though was going into the bios and disabling ACPI all together. Computer does not stutter but of course it will not poweroff by itself etc.

---

