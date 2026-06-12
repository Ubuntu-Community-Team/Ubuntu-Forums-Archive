---
title: "DMA killed my cdrom....?"
date: 2006-03-26
forum: Desktop Environments
---

### Post by deathbyswiftwind on 2006-03-26
I need some major help. I used automatix to turn on dma and now my cdrom after it reads the first cd I have in the drive the rest of the time the names come out like ????? or something along the lines. It always displays the title of the cd but it never will give the contents Ive tried cleaning all my cds as well as using a cleaner for the lens and all I can figure is that turning on dma did it. So can I uninstall the dma mode?

---

### Post by arnieboy on 2006-03-26
please paste the results of 
```
cat /proc/cpuinfo
```

---

### Post by deathbyswiftwind on 2006-03-26
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : Mobile AMD Athlon(tm) 64 Processor 3200+
stepping        : 10
cpu MHz         : 801.788
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 1589.24

---

### Post by arnieboy on 2006-03-26
Thanks. now please paste the results (if any) of the following:
```
lspci | grep "VIA Technologies"
```

---

### Post by deathbyswiftwind on 2006-03-26
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by arnieboy on 2006-03-26
great now do the following:
```
sudo gedit /etc/modules
```
delete the following lines:
> via82cxxx
ide-cd
ide-disk
ide-generic
save and exit.
now do 
```
sudo gedit /etc/hdparm.conf
```
and delete the following lines from the end:
> /dev/cdrom {
       dma = on
}

save and exit and reboot.

DMA will be removed.

---

### Post by deathbyswiftwind on 2006-03-26
thanks for your help

Id also like to say I do love your program with it I can get my computer setup in a matter of an hour when it used to take around 4

---

