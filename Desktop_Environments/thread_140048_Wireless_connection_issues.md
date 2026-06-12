---
title: "Wireless connection issues"
date: 2006-03-05
forum: Desktop Environments
---

### Post by surfingchimp on 2006-03-05
HI Guys, 

I am new to Ubuantu, but have used Linux on and of over the past few years. 

I am really enjoying my Ubuantu experience except........

My Wireless network can't seem to connect. under Advanced>Network settings it displays my wireless network card, and says active but I can't seem to connect.
I have tryed everything, added the .INF driver via the Windows driver utility and that says everything is OK. turned off wireless security, turned it on, no joy I really feel I have exhausted all avenues. 
The problem seems to be obtaining an IP address, thereis nothing wrong with the router becasue my windows box is wireless aswell and that has no trouble.
other question, there is a lack of wireless encryption settings, does it default to 128bit WEP encryption or????
can anyone help me out here plz.

---

### Post by Ramses de Norre on 2006-03-05
Does your router has mac control enabled? If so, add the mac addres of your wifi card to the allow list or turn mac control off.
Can you ping the router?

For the wep: it didn't work for me through the gui, but you can simply add a line to /etc/network/interfaces ```
wireless-key #######

```
64 or 128bit depends on how many characters you fill in there.

---

### Post by surfingchimp on 2006-03-05
I checked that file and edited it directly although the settings were correct to a degree.

still have no connection, which is annoying. other tips would be greatly appreciated

---

### Post by Ramses de Norre on 2006-03-05
You say your windows box has no troubles, is it another pc?
If so, did you check the mac control?

---

### Post by surfingchimp on 2006-03-05
it's the same machine, I have a removeable HD, so the MAC address will be the same.

I have now also tryed to turn DHCP off on my router and assign the IP address manually but ot no luck.

this has got to be something simple, everything looks as if it SHOULD work, but just doesn't

---

### Post by Ramses de Norre on 2006-03-05
Can you post your /etc/network/interfaces and the outputs of ifconfig and iwconfig?

---

### Post by surfingchimp on 2006-03-05
hi, sorry for the delay, I had to get away from my PC for a bit

here is the info you requested:

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:off/any  Nickname:"Home Net"
          Mode:Auto  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

> 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2859023 (2.7 MiB)  TX bytes:2859023 (2.7 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:0E:0D:8A:CD
          inet6 addr: fe80::212:eff:fe0d:8acd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet dhcp
	network 192.168.2.1
	broadcast 192.168.2.255
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid Home Net
	wireless-key1 s:7b1bb527fd
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.2.1
	wireless-key s:7b1bb527fd

auto wlan0


many thanks for your help, hopefully we can get a soloution on this

---

### Post by zapcojake on 2006-03-05
Are using a Belkin router? I am having exactly the same trouble you are with 7230-4 and an airnet awd154 using ndiswrapper.  Even if i use the wireless router as a wap plugged into my trusty IPcop router it won't connect.

---

### Post by PhragMunkee on 2006-03-06
I've had the exact same problems as documented **[here](http://ubuntuforums.org/showthread.php?t=135447)**.  Unfortunately, that call for help didn't result in any responses.

Since then, I have re-installed Windows XP Home (that shipped with the laptop) and have had no problems.  And, currently, I am running Vista Beta 2 (my laptop is obviously my test bed).  I also tried re-installing Ubuntu somewhere between XP and Vista and still could not get connected to the wireless.  Windows works just fine as does my roommate's iPowerBookMacG^2Whatever laptop.

And, being fed up with Vista's painfully poor performance, I'll be re-installing Ubuntu once again in about 5 minutes (as soon as I find the CD).

---

### Post by surfingchimp on 2006-03-06
yes I am using a (crappy) Belkin router, I am moving home next week and will be using my other (why do I do it to my self) Belkin router which is a different model, hopefully I'll have more joy with that 1

---

### Post by Ramses de Norre on 2006-03-06
> Access Point: 00:00:00:00:00:00
I think that's the problem.
What does sudo iwlist wlan0 scan give?

---

