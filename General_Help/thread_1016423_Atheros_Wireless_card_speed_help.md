---
title: "Atheros Wireless card speed help"
date: 2008-12-19
forum: General Help
---

### Post by Twitch6000 on 2008-12-19
Okay well I know this is probably not a new help me and I just have not looked hard enough,but I am going to ask anyways..

My atheros card is downloading updates and software very slow.

Surfing the web and such however is fine.

When I am on my windows machine the downloading is about 1mb-2mb max and 500kb average.(not kidding)

On my Linux side it feels like I am on dial up lol...

I have tried a few tweaks and such like ip6,changing servers,and removing anything not needed.

None have helped much..

I know it is not ubuntu either as my brother is using it just fine and downloading stuff blazing fast.

So I know it is something about the wireless card and just need to fix it =[.

---

### Post by Mikecore on 2008-12-19
Check your connection info and see what speed your set at my is 54mb/s so should your the Atho sometimes connects at 1mb/s and you have to set the rate before you bring up the card

---

### Post by Twitch6000 on 2008-12-20
> **Mikecore said:**
> Check your connection info and see what speed your set at my is 54mb/s so should your the Atho sometimes connects at 1mb/s and you have to set the rate before you bring up the card

Ahh yes I did see something around the forums on this before..

I will check this and if this is my problem, how would I go about fixing?

Edit: Oh here is some helpful info I should have gave earlier :/.

twitch@twitch-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Device 0845 (rev a2)
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by Twitch6000 on 2008-12-20
Arghh found the problem.. it is only 1mb speed right now :(

from the terminal -

iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:10:51:A7:E3   
          Bit Rate=1 Mb/s   Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=42/100  Signal level:-68 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


How to fix :(

---

### Post by glepore70 on 2008-12-21
First you can do:
iwlist scan
to see what rates are supported by your access point.
Next, run:
sudo iwconfig wlan0 rate 18M
to set your card to a higher rate. You may have to try various rates to hit one that your card supports (as well as the access point.)
To make the change permanent, I added this to my /etc/network/interfaces (after the iface line):
pre-up iwconfig wlan0 rate 18M

good luck!

---

### Post by Twitch6000 on 2008-12-22
> **glepore70 said:**
> First you can do:
iwlist scan
to see what rates are supported by your access point.
Next, run:
sudo iwconfig wlan0 rate 18M
to set your card to a higher rate. You may have to try various rates to hit one that your card supports (as well as the access point.)
To make the change permanent, I added this to my /etc/network/interfaces (after the iface line):
pre-up iwconfig wlan0 rate 18M

good luck!

Well I know my router(wrt54g linksys) supports up to 54M).

I will try as suggested and see what happens after installing Linux Mint 6(yeah yeah I am on a distro hopping spree again :/)

---

### Post by Twitch6000 on 2008-12-22
Okay I tried what you said to do and it is still saying 1mb :/.

I did the mb scan thing and it says it supports 18 and 48mb and I tried,both failed.

What should I try now?

Edit: okay I think I got it working... It is dling a bit faster (half a mb)

Now if I can get it downloading like normal I will be happy :).

---

