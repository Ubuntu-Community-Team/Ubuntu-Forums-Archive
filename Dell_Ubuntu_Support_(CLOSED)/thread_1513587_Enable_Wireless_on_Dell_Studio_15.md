---
title: "Enable Wireless on Dell Studio 15"
date: 2010-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zeiger on 2010-06-19
Hey guys,
I recently ordered a Dell Studio 15 with the following wireless card:
Wireless : European Intel Wireless 6200 (802.11a/b/g/n 2X2) LAN-Card

I wanted to install Ubuntu 10.04 along with the pre-existing Windows 7, so I used "wubi" and it worked out very well.
After installing, I could connect to my home wireless network and do a lot of things. I decided to install the ATI Graphic Card drivers (automatically found by Ubuntu) so that I could use Compiz etc. and downloaded them using the wireless network. After installing the drivers successfully, I restarted the laptop and everything worked well except that the "Enable Wireless" option was grayed out.
Now I don't know know to to enable this, I tried using the keyboard key which I use to enable/disable wireless in Windows 7, but it did not work in Ubuntu.

Any help?
Thanks,
Zeiger.

---

### Post by JosephLynch743 on 2010-06-19
Zeiger,
I am not sure how much help I can be but I had a very similar problem with my studio 14z.  My issue was that after I installed the NVIDIA drivers with the "Hardware Drivers" utility under administration it killed the wireless drivers.  I reinstalled Ubuntu and instead of using that utility downloaded the drivers from NVIDIA's website and installed them in "init 1" as root instead of with the utility which managed to fix the issue.  I am not sure of ATI's drivers but NVIDIA's will remove existing configurations so the reinstall was probably unnecessary.  If you think this is an option you wish to persue all you need to do is go into terminal and type sudo init 1 and enter your password.  Eventually you will see a blue screen which will have a gray box.  Scroll down to root and then cd to the proper folder.  After this I used the command sh thenthefilenamehere.  I do hope that this helps but I apologize if this does not.

Cheers,
Joseph

---

### Post by zeiger on 2010-06-19
While in Windows 7, I press the F2 key to toggle Wireless On, Off.
That does not seem to have any effect in Ubuntu 10.04, although all other keys (like increasing brightness, volume etc.) work well in Ubuntu.

Is there no way to manually enable the Wireless Adaptor?

---

### Post by zeiger on 2010-06-19
Ok I finally figured it out.
This [link]("http://ubuntuforums.org/showpost.php?p=5024425&postcount=1") helped me.

Basically, because I use dual boot, Windows 7 was "turning off" the wireless adaptor whenever I restarted/powered down my laptop. So the adaptor was not available in Ubuntu.
I went to the Power Management section of the Wireless Adaptor in Windows and unticked the option "Allow the computer to turn off this device to save power" and voila, Wireless is now working in Ubuntu.

Stupid MS thinks powering down a laptop is the same as running on a low battery!

---

### Post by zeiger on 2010-06-20
Oh these woes don't seem to end.
I started my laptop today and again, Wifi not enabled in Ubuntu.

The following is an output of the command```
 sudo lshw -c network
```:

```
jigarprachi@ubuntu:~$ sudo lshw -c network
[sudo] password for jigarprachi: 
  *-network DISABLED      
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:87:07:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:37 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:70:af:36
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)


```The command ```
sudo ifconfig wlan0 up
``` doesnt help either.

Any help here please?

---

### Post by jxtreme on 2010-06-20
I have a Studio 15 as well, and I had the same problem when I first installed Lucid. Plug your laptop into your router via ethernet to get online. Then go to System>Administration>Hardware drivers and activate the Broadcom STA wireless driver and reboot. Hope this helps!

---

### Post by wojox on 2010-06-20
> **jxtreme said:**
> I have a Studio 15 as well, and I had the same problem when I first installed Lucid. Plug your laptop into your router via ethernet to get online. Then go to System>Administration>Hardware drivers and activate the Broadcom STA wireless driver and reboot. Hope this helps!

This is what I did as well for my Dell Studio. After that on the top panel right click the network manager applet and configure it.

---

### Post by zeiger on 2010-06-21
But will the Broadcom STA wireless driver work with my Intel Wireless 6200 (802.11a/b/g/n 2X2) card?

---

### Post by jxtreme on 2010-06-21
> **zeiger said:**
> But will the Broadcom STA wireless driver work with my Intel Wireless 6200 (802.11a/b/g/n 2X2) card?
If it shows up in Hardware Drivers, then yes. It can't hurt to try.
EDIT: It might be a different driver, I have a Broadcom card. But you probably need a proprietary driver.

---

### Post by zeiger on 2010-06-21
It does not show up in the System>Administration>Hardware drivers list. There I get only my ATI Video Card driver and I already installed it.

There is a wireless toggle switch on the keyboard, along with the F2 key. It doesn't seem to enable Wireless. Whereas in Windows 7 (I use dual boot), it does.

---

### Post by jxtreme on 2010-06-21
If you uninstall the ATI driver, does wifi come back? The driver for your wireless card is actually included in the kernel.

---

### Post by zeiger on 2010-06-21
I did the following:
1. Uninstall the ATI Video Drivers, still "Enable Wireless" was grayed out
2. Rebooted laptop after the Video Driver uninstall, still "Enable Wireless" was grayed out
3. Logged onto Windows, uninstalled Ubuntu using wubi. Then re-installed Ubuntu using wubi. Now logged into Ubuntu, still "Enable Wireless" was grayed out

:confused:

Sometimes, when I keep F2 (Wireless icon on the F2 key) pressed on for a long long time, or if I keep pressing F2 again and again for a long time, Wireless is enabled suddenly. But this trick doesn't work always. The next time I restart, its gone again.

---

### Post by jxtreme on 2010-06-21
If you boot from a live cd, do you have this problem? I'm wondering if it has to do something with wubi and Windows 7.

---

### Post by zeiger on 2010-06-22
For now, I run the following command from Terminal, when I start up Ubuntu and the wireless comes back to life without any problems:

```
sudo rmmod -f dell_laptop
```

---

### Post by jxtreme on 2010-06-22
As a workaround, go to System>Preferences>Startup Applications and click add. Give the task a name, paste the command in, and add it. That way, every time you start Ubuntu it'll make your wireless turn on.

---

### Post by SitarHER0 on 2010-07-14
The command from zeiger works and gets my wireless working every time Ubuntu boots. (I have exactly the same problem on a Dell studio 15 with Ubuntu installed by wubi). However, the workaround using Startup Applications doesn't fix it. Does it have something to do with the [FONT=Courier New]sudo[/FONT] at the start?

---

### Post by zeiger on 2010-07-16
Hi SitarHERO,
I tried to put the command as a startup script as well, but it seems "sudo" is not a good idea for an automated startup command.

For now, and until the time this gets resolved, I just run a .sh file with my working command in it.

Good to know that I am not the only one with this problem :D

---

### Post by jarviser on 2010-07-18
> **jxtreme said:**
> If you boot from a live cd, do you have this problem? I'm wondering if it has to do something with wubi and Windows 7.
It would be interested if the people with this problem tried the live boot. Some things such as hibernation will not work under Wubi so it's not beyond possibility that this is as a result of Wubi.

Personally (and if the above works)  I would do a proper dual boot install and dump Wubi. I would never let Windoze "help" me with installing Linux! I can see why it was written to help people install from a comfortable scenario but it seems to cause a lot of problems in these pages.

---

### Post by SitarHER0 on 2010-07-19
> **zeiger said:**
> 

For now, and until the time this gets resolved, I just run a .sh file with my working command in it.


Sorry, but as a complete newbie to Ubuntu, could you tell me how I could make a .sh with this in?
Thanks a lot :)

---

### Post by ashishmody on 2010-08-19
I have the same problem on a Dell Studio 15 running Windows 7 and Ubuntu. It works with the rmmod command specified here. Any further updates on this?

---

### Post by merry_meerkat on 2010-08-22
Perhaps try what is outlined here:
[http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/](http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/)

---

### Post by tetralectic on 2010-08-24
> **merry_meerkat said:**
> Perhaps try what is outlined here:
[http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/](http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/)
Thanks for this link and thanks to the author of this article. This worked like a charm on my Dell E4300 laptop when, after an update today, the wireless just stopped working.

:p

---

### Post by siyabonga on 2010-09-19
I'm also having trouble with wireless on a Dell Studio 15. However, I'm using Xubuntu 9.04, installed inside Windows 7 (had trouble booting from CD). I changed the power settings for the network adapter in Windows, as suggested, but this made no difference.

Zeiger's suggestion doesn't help since I don't have a dell_laptop file. Should I try Xubuntu 10.04?

In case this helps, here's the output of lshw -c network and ifconfig
```
siyabonga@ubuntu:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: f0:4d:a2:46:fb:5c
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:91:90:50:3a:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

siyabonga@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:46:fb:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:244 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

```

---

### Post by siyabonga on 2010-09-24
I finally managed to sort out my problem by following the advice given [here]("http://ubuntuforums.org/showthread.php?t=1405820&highlight=driver+6200&page=2")

Now if only I can figure out how to change the screen resolution and get sound working...

---

### Post by merry_meerkat on 2010-09-27
> I finally managed to sort out my problem by following the advice given here

Thanks siyabonga. Could you tell us the specific post number in that thread that contains the solution?

---

### Post by siyabonga on 2010-09-29
> **merry_meerkat said:**
> Thanks siyabonga. Could you tell us the specific post number in that thread that contains the solution?

Sorry, I should have mentioned that. It's post #15, upgrading the kernel. I should also add that I'm using Xubuntu 9.10 now.

---

