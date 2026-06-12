---
title: "RTL8139D does not work in Ubuntu"
date: 2010-06-11
forum: Desktop Environments
---

### Post by Satty_dey on 2010-06-11
Hi, I've installed ubuntu-10.04-desktop-i386 in my desktop. I cannot get the Ethernet Card to work. Below are the infos:
```
$ uname -a
Linux mousumi-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

```
$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 8
model name	: AMD Athlon(TM) XP 1800+
stepping	: 0
cpu MHz		: 1536.909
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
bogomips	: 3073.81
clflush size	: 32
cache_alignment	: 32
address sizes	: 34 bits physical, 32 bits virtual
power management: ts
```

```
$ lspci
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce AC'97 Audio Controller (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:06.0 Non-VGA unclassified device: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
```

```
$ lspci -n
00:00.0 0600: 10de:01a4 (rev b2)
00:00.1 0500: 10de:01ac (rev b2)
00:00.2 0500: 10de:01ad (rev b2)
00:00.3 0500: 10de:01aa (rev b2)
00:01.0 0601: 10de:01b2 (rev c3)
00:01.1 0c05: 10de:01b4 (rev c1)
00:02.0 0c03: 10de:01c2 (rev c3)
00:03.0 0c03: 10de:01c2 (rev c3)
00:05.0 0401: 10de:01b0 (rev c2)
00:06.0 0401: 10de:01b1 (rev c2)
00:08.0 0604: 10de:01b8 (rev c2)
00:09.0 0101: 10de:01bc (rev c3)
00:1e.0 0604: 10de:01b7 (rev b2)
01:06.0 0000: 1904:8139
02:00.0 0300: 10de:01a0 (rev b1)
```

```
$ lsmod | grep 8139
8139cp                 16186  0 
8139too                18545  0 
mii                     4381  2 8139cp,8139too
```

```
$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12208 (12.2 KB)  TX bytes:12208 (12.2 KB)
```

```
$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
```

Can anyone please let me know how to solve this?

Thanks in advance

---

### Post by pytheas22 on 2010-06-11
Please try running:
```

sudo modprobe sc92031
```

I got this from [here]("http://www.uluga.ubuntuforums.org/showthread.php?p=8839866").  Apparently the issue has to do with your particular ethernet card being a "fake Realtek" card, whatever that means, and Ubuntu tries to use the wrong driver as a result.

If the command above doesn't solve the problem for you, please post the output of:
```

dmesg | grep -e 8139 -e sc92 -e eth
ifconfig -a
```

---

### Post by Satty_dey on 2010-06-12
Thanks for the quick reply :)

Situation stands like this now:

lspci shows the same output.

```
~$lsmod | grep sc
sc92031      11384       0

```
```
~$ dmesg | grep -e 8139 -e sc92 -e eth
[    8.963932] 8139too Fast Ethernet driver 0.9.28
[    9.482256] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   69.355532] sc92031 0000:01:06.0: device not available because of BAR 1 [0x00-0x0f] collisions
[   69.355551] sc92031: probe of 0000:01:06.0 failed with error -22

```
```
~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)
```

Please let me know what needs to be done.

---

### Post by pytheas22 on 2010-06-12
These lines from dmesg seem to be the problem:
```

[   69.355532] sc92031 0000:01:06.0: device not available because of BAR 1 [0x00-0x0f] collisions
[   69.355551] sc92031: probe of 0000:01:06.0 failed with error -22
```

Unfortunately I'm not sure what that means, and googling doesn't help much.  Do you see the same output in dmesg if you do a full reboot, and avoid loading the 8139too and 8139cp drivers?

It probably actually wouldn't hurt to blacklist those drivers, since they're not actually capable of driving your device, by running:
```

echo blacklist 8139too | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist 8139cp | sudo tee -a /etc/modprobe.d/blacklist.conf
```

That way they won't interfere with anything.

---

### Post by Linuxforall on 2010-06-12
This is among the most common chips used by many for LAN, have been using this since eons when I first started with desktop Linux way back in 1999.

---

### Post by pytheas22 on 2010-06-12
> This is among the most common chips used by many for LAN, have been using this since eons when I first started with desktop Linux way back in 1999.

What is the lspci -nn output for your device?  I think the original poster's ethernet card is either being misidentified by lspci (unlikely) or it's non-standard hardware.  Something strange is going on because it doesn't seem at all to be a Realtek card.

By the way, Satty_dey, did you buy this ethernet card from somewhere and install it yourself?  If it came with your computer, who built your computer?  I've seen cases where people have bought wireless cards on ebay that are not actually the hardware they purport to be.

---

### Post by Satty_dey on 2010-06-13
I've blacklisted the drivers as suggested.

lspci -nn shows the following after reboot:

```
01:06.0 Non-VGA unclassified device [0000]: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor [1904:8139]
```

Yes I got this ethernet card from a friend and trying to install myself.

---

### Post by Satty_dey on 2010-06-13
ok, I've changed my card to a DLink Ethernet card.

lspci -nn now shows the following:

```
01:06.0 Ethernet Controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine III] [1106:3106] (rev 86)
```

Ifconfig -a still shows only lo

---

### Post by pytheas22 on 2010-06-13
That second card should be driven by the via-rhine driver.  Does it appear in ifconfig if you run:
```

sudo modprobe via-rhine
```

If not, what is the output of:
```

dmesg | grep -e via -e eth
```

after running that command?

---

### Post by Satty_dey on 2010-06-13
After sudo modprobe via-rhine ifconfig -a shows the same output.

```
~$ dmesg | grep -e via -e eth
[    1.318717] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.319278] via-rhine 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, high) -> IRQ 18
[    1.320487] via-rhine: probe of 0000:01:06.0 failed with error -5
```

---

### Post by Satty_dey on 2010-06-13
BTW it was a windows XP installation which I formatted and installed Ubuntu, if that throws any light

---

### Post by pytheas22 on 2010-06-13
It seems like your system doesn't like the VIA card either.  You are having bad luck!

But let's try using the Windows driver to get the card running, instead of the Linux one which doesn't seem to work well.  You can do this using ndiswrapper (traditionally ndiswrapper is used to get wireless cards running, but it usually works for ethernet devices too).  These are the commands you'll need (hopefully you can get your computer connected to the Internet somehow for running these commands; if not let me know):

```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://www.viaarena.com/Driver/via_rhine_ndis5_v384a.zip
unzip via_rhine*
sudo ndiswrapper -i VIA_Rhine_NDIS5_V384A/X86/FETNDIS.inf 
```

After this, try running these commands to remove the Linux driver and insert the Windows one:
```

sudo rmmod via-rhine
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Don't worry if you get an error message similar to "Module XXXX does not exist in /proc/modules"; just proceed to the next command.

At this point you will hopefully finally have an ethernet device recognized by ifconfig.  If you still don't, please post the output of:
```

dmesg | grep -e ndis -e eth
ndiswrapper -l
```

---

### Post by Satty_dey on 2010-06-14
ok heres the result:

I had ndiswrapper installed previously.

I downloaded and installed the driver, did the rmmods as suggested.

Now lspci has stopped detecting the card. ifconfig -a obviously shows the same output as before :(

---

### Post by pytheas22 on 2010-06-14
That's really weird.  ndiswrapper should not cause lspci to stop seeing that the hardware is present for any reason that I can think of.  If you rmmod the ndiswrapper module, does lspci start seeing the ethernet card again?

Are you sure there's not a hardware issue with your motherboard?  That might explain why you're experiencing such weird behavior: I've never seen anyone have this hard of a time getting an ethernet card working.  Have you tried all the PCI slots?

---

### Post by Satty_dey on 2010-06-15
ok I got it working. it seems even if I removed the via-rhine driver using rmmod, it was still sitting there. So I removed it once and more and restarted the machine. The network card was detected and it automatically connected to the DHCP network and internet. But but but, this is just only once, then the machine hanged. I restarted the machine and it went back to the previous situation.

Now I see the via-rhine driver again, and even if I do sudo rmmod via-rhine, after restarting the machine, lsmod grep via shows the via-rhine again.

How can I permanently remove it?

---

### Post by pytheas22 on 2010-06-15
You can blacklist via-rhine by adding the line:
```

blacklist via-rhine
```

to the file /etc/modprobe.d/blacklist.conf.

If for some reason that doesn't work, you can delete the module once and for all by running:
```

sudo rm /lib/modules/`uname -r`/kernel/drivers/net/via-rhine.ko
```

---

### Post by Satty_dey on 2010-06-17
Don't know whats going on. Did everything that you said but it keeps coming back after restart. It does not find the via-rhine.ko when modprobe via-rhine is executed after deleting the file. However lsmod | grep rhine still lists via-rhine.

---

### Post by pytheas22 on 2010-06-17
hmmm, what's the output of:
```

sudo updatedb
locate via-rhine.ko
```

---

### Post by Satty_dey on 2010-06-26
Sorry for responding late. I seem to have discovered the issue. I've blacklisted via-rhine. However each time I restart I've to run the followings:

```
sudo rmmod via-rhine
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Then the network connects. How can I skip this step?

One more issue is that I cannot browse any site and it always says timed out. What could be the issue here?

---

### Post by pytheas22 on 2010-06-26
> How can I skip this step?

The easiest solution is probably to write a boot script to run those commands automatically each time you turn on the computer.  There are instructions [here]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") for writing a boot script in Ubuntu; please give them a try and let me know if you have any trouble.
> 
One more issue is that I cannot browse any site and it always says timed out. What could be the issue here?

I guess that is an issue!  The first thing I'd check would be for DNS issues; to do that, see if putting an IP address (such as 72.14.204.103, for Google) into the address bar instead of a URL works.

If DNS doesn't seem to be the problem, or if you can't connect even to an IP address directly, see if you can ping your gateway or other computers on your subnet.  If you can't send traffic anywhere, there may be a driver issue still...

If you don't know what I mean by pinging your gateway etc., let me know and I can be more specific...but you seem to know what you're doing so I won't be pedantic :)

---

### Post by Satty_dey on 2010-06-27
Well even putting IP address in the browser doesn't open the page. My gateway 192.168.1.1 is sometime getting pinged and sometimes says Destination Host Unreachable.

---

### Post by pytheas22 on 2010-06-27
In consistent behavior like that is bizarre.  Do you see anything in dmesg that might be relevant?  It's possible the ethernet settings might be off; otherwise, it may help to install a different version of the Windows driver into ndiswrapper (that is, try using, for example, the Windows 2000 drivers instead of the XP ones, or use version 2 of the driver instead of version 3).

---

