---
title: "ubuntu shuts down out of the blue!"
date: 2009-03-07
forum: General Help
---

### Post by shane2peru on 2009-03-07
Help, this is serious!  I thought my harddrive was failing for real.  But it seems to be only Ubuntu.  I'm a long time ubuntu user and have never faced this before.  My computer will just shutdown for no reason.  It has done this to me only in the past 9 day.  It randomly shuts down on me.  For no apparent reason.  This is about the 5th time it has done this, and now it will not boot back into Ubuntu.  It just hangs really bad on booting, and nothing happens.  I have a Toshiba Satellite laptop with ATI drivers.  I have the ATI drivers installed from their site, but they have been installed a long time.  I booted into windows vista, and it seems to run fine, however all my work is in Ubuntu!  Not windows.  I do have my system backed up, so I'm not afraid of loosing data, but this is odd!  Anyone else run into anything like this?  What can I do to trouble shoot it and find out what the problem is?

Shane

---

### Post by LoneWolfJack on 2009-03-07
Did you check whether your CPU or GPU is overheating? Perhaps you just recently activated compiz or something?

Other than that, does your error log say something that seems fishy?

```
gedit /var/log/messages
```

---

### Post by shane2peru on 2009-03-07
> **LoneWolfJack said:**
> Did you check whether your CPU or GPU is overheating? Perhaps you just recently activated compiz or something?

Other than that, does your error log say something that seems fishy?

```
gedit /var/log/messages
```

At the moment I'm not able to boot into Ubuntu, and I don't have a disk with me to check. :(   I'm not even sure I have a recent Ubuntu disk since we just moved.  This is really bad.  I started downloading Ubuntu Intrepid 64bit (which is what I was using).  I guess we will see.

Shane

---

### Post by shane2peru on 2009-03-08
Ok, more info.  I checked the logs, there was nothing that indicated overheating.  Although that is what I´m guessing is the problem.  The odd thing is I can run in Windows Vista for hours and it has no problem.  Ok, I don´t have any programs to run in Vista in reality, and can´t do any work, so I don´t ever give the computer a work out.  However in Ubuntu Hardy Live CD I ran it for about 30 minutes and it shutdown for no apparent reason.  I ran Ubuntu Intrepid (live usb) and it also shutdown out of the blue.  It seems as though I cannot run any Ubuntu version that I have, live CD or installed because the computer just shuts down.  It is a AMD processor, which tend to run a little hotter than Intel processors (at least that is my understanding).  This probably a hardware problem that is caused by the way that Ubuntu access or runs versus how Windows runs.  I do not like windows and cannot go back to working on Windows, so please any input would greatly be appreciated.  I thought about downgrading to Hardy, but after my test of the live CD I don´t think that is going to solve the problem.  I cannot run Ubuntu more than 30 min while Vista will run for several hours.  For kicks in Vista I did a virus scan and did a defragmentation just to try and warm it up and get it to shut down.  No such luck.  Any help would greatly be appreciated!!!

Shane

---

### Post by shane2peru on 2009-03-09
Does anyone have any ideas?  Does anyone know how to adjust the laptop fan to keep it running on high always?  I´m just guessing this is the problem, I really don´t know.  It is worth a shot.  Thanks.

Shane

---

### Post by shane2peru on 2009-03-09
Ok, here seems to be a page that has some relevant boot options I´m going to try out.  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Shane

---

### Post by mªrty on 2009-03-09
If the liveCD shutdown for no apparent reason as well, then I'm pretty sure we can say that the cause is hardware. Was the liveCD x86_64 as well? try a 32bit liveCD if you are able and see if that shuts itself down.

---

### Post by miegiel on 2009-03-09
My vote is on hardware, something cooling or power related, but it's just a hunch.

If you still haven't pin pointed the problem by bed time you can let it run a memtest and see how it coped with that when you wake up. It's on the live CDs and as an option in the grub menu.

You can read temperatures with "lmsensors" and "hddtemp", they're in the ubuntu repos.

To give you an idea:
```
:~$ sudo hddtemp /dev/sda
[sudo] password for ********: 
/dev/sda: WDC WD5000AAKS-00A7B0: 44°C
```
```
:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +18.0°C                                    
Core0 Temp:  +20.0°C                                    
Core1 Temp:  +15.0°C                                    
Core1 Temp:  +16.0°C                                    

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.07 V  (min =  +3.95 V, max =  +3.70 V)
VDDR:        +1.28 V  (min =  +0.82 V, max =  +4.08 V)
+3.3V:       +3.33 V  (min =  +3.54 V, max =  +1.39 V)
+5V:         +4.97 V  (min =  +5.99 V, max =  +4.06 V)
+12V:       +12.10 V  (min = +16.19 V, max = +15.81 V)
in5:         +1.18 V  (min =  +3.50 V, max =  +4.08 V)
in6:         +2.13 V  (min =  +2.03 V, max =  +4.02 V)
5VSB:        +4.87 V  (min =  +3.23 V, max =  +6.80 V)
VBat:        +3.33 V
fan1:       1355 RPM  (min = 3245 RPM)
fan2:          0 RPM  (min = 3245 RPM)
fan3:          0 RPM  (min = 3245 RPM)
temp1:       +34.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermal diode
temp2:       +44.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
temp3:       +47.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
cpu0_vid:   +1.550 V
```

---

### Post by shane2peru on 2009-03-09
ok, this is a acpi and overheating problem that is common to Toshiba and Linux in general.  It seems as though the Toshacpi stuff is not enabled on this kernel for Ubuntu, which is causing problems. 

I'm trying with noacpi on the kernel to see how that works.  The acpi=force only gave me 30 minutes then a shutdown.  when I run ```
cat /proc/acpi/fan/* 
```  the fan is not detected.  Neither is the battery.  What a mess.  Any ideas would be greatly appreciated.  

I did install hddtemp and it seems to be running at 29C at the moment, and stable with noacpi in the kernel line as an option.  I guess we will see.  I think I need an acpi specialist. :)

Shane

**EDIT:**  oops.  I mean I run acpitool -f and no fan is recognized.  I run acpitool -B and battery slot is empty.  This is a problem.

---

### Post by shane2peru on 2009-03-09
Ok, seems like noacpi option is helping.  I think.  At any rate seems there is a discrepancy between hddtemp and sensors, here is the output of both one right after the other:

```

hddtemp /dev/sda
/dev/sda: TOSHIBA MK2552GSX: 31°C

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +69.0°C  (crit = +105.0°C)                  


```
I put lmsensors right on my panel to constantly monitor them.  

Shane

---

### Post by mªrty on 2009-03-09
> **miegiel said:**
> You can read temperatures with "lmsensors" and "hddtemp", they're in the ubuntu repos.

To give you an idea:
```
:~$ sudo hddtemp /dev/sda
[sudo] password for ********: 
/dev/sda: WDC WD5000AAKS-00A7B0: 44°C
```


Your Hard drive is at 44 °C? That seems really high (though I haven't run lmsensors or hddtemp on my own computers.
I didn't even know hdds could read temp! :D

---

### Post by miegiel on 2009-03-09
> **mªrty said:**
> Your Hard drive is at 44 °C? That seems really high (though I haven't run lmsensors or hddtemp on my own computers.
I didn't even know hdds could read temp! :D

44C is a bit high, but not to high. A disk in a cooler part of my case is running at 35C.

---

### Post by shane2peru on 2009-03-09
> **shane2peru said:**
> Ok, seems like noacpi option is helping.  I think.  At any rate seems there is a discrepancy between hddtemp and sensors, here is the output of both one right after the other:

```

hddtemp /dev/sda
/dev/sda: TOSHIBA MK2552GSX: 31°C

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +69.0°C  (crit = +105.0°C)                  


```
I put lmsensors right on my panel to constantly monitor them.  

Shane

Ok, I figured out what the apparent discrepancy is, one is hdd temp other seems to be the processor temp, which obviously run at different temps. :)  The noapci option seems to be working like a champ, that was the ticket!  Thanks for the replies.  

If anyone needs this I added the red text to my /boot/grub/menu.lst
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		9d9e8656-7293-4bfc-84be-21bfaacea451
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9d9e8656-7293-4bfc-84be-21bfaacea451 ro quiet splash [COLOR="Red"]noacpi[/COLOR]
initrd		/boot/initrd.img-2.6.27-11-generic



```

Hope this helps someone.

---

