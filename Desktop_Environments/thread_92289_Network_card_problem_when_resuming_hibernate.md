---
title: "Network card problem when resuming hibernate"
date: 2005-11-19
forum: Desktop Environments
---

### Post by mvnet on 2005-11-19
I installed Ubuntu Breezy 5.10 on my laptop (Packard Bell IGO 2451). Installation went fine and nearly everything works - even my touchpad and my WLAN-card (D-Link DWL-G650+). My WLAN-card uses ndiswrapper as driver (it emulates my card's WinXP drivers). I also use wpa_supplicant because I use WPA-encryption.

I even got hibernation work somehow. **The problem is that when I resume from hibertnate my WLAN card stops responding.** The two lights on my card are not on as usually and my wireless network doesn't work. I know that Ubuntu automatically stops ndiswrapper and PCMCIA cards when I choose to hibernate and it tries to bring then back when I resume from hibernate. But as I said resume doesn't work fine. The only way to get wireless network back is to reboot my laptop.

The same thing happens when I run these commands:

(So first stop network, stop ndiswrapper and stop PCMCIA-card)
```
sudo ifdown wlan0
sudo rmmod ndiswrapper
sudo cardctl eject 0
```

(Then try to get network back on line)
```
sudo cardctl insert 0
sudo modprobe ndiswrapper
sudo ifup wlan0
```

But as I said, network won't work after this.

But if I do this:

```
sudo ifdown wlan0
sudo cardctl eject 0
```

(So now the PCMCIA car is stopped and lets bring it back)

```
sudo cardctl insert 0
sudo ifup wlan0
```

Wireless network works now. So if i don't stop ndiswrapper it works. I tried to modify files resume.d and prepare.d in acpi folder and tried to disable that Ubuntu will shutdown ndiswrapper when hibernating but it didn't work. Hiberate didn't work at all after that.

Usually when my wireless network works and when i run "iwconfig" command it prints out this:

[I]koti@kannettava:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Kotiverkko54Mbps"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:A7:7D:0A
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr: 4096 B
          Power Management: off
          Link Quality:100/100  Signal level:-48 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/I]


But after resuming from hibernation/sleep it prints out this:

[I]koti@kannettava:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STA15A416"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Channel:1  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]

So SSID and Access point are wrong and there is some strange parameter Nickname:"acx100 v0.2.0pre8".

It looks like Ubuntu starts using it's own drivers for the PCMCIA card when ndiswrapper has been stopped, am I right? Or has this got something to do with wpa_supplicant?

So how can I resume from hibernate/sleep so that my WLAN card will work?

(Sorry about my bad english) :D

---

### Post by mvnet on 2005-11-19
Can't anyone help?

---

### Post by mvnet on 2005-11-28
Problem is now solved. Ubuntu loaded automatically acx100 driver (instead of ndiswrapper) for my wlan card when I resume from hibernate. 

I edited "/etc/hotplug/blacklist" and added two following lines in the file:
```
acx100
acx_pci
```

After that reboot and wlan card works after resuming from hibernate.
So now Ubuntu doesn't anymore load acx100 driver when resuming hibernate. It loads ndiswrapper as it should.

---

