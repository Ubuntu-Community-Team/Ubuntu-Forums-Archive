---
title: "No internet connection"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Vinze on 2005-12-28
My internet has just been reconnected, so I started up my computer expecting to be able to get on the internet again, but it didn't work! I tried both in Xfce, my default, and in GNOME, but it just didn't work! I am sure I had all settings set correctly. It just kept saying I didn't have an IP, while I set DCHP.

When I'm on Windows (which I'm now, had to try six times before I got it to work :rolleyes: ) and there it just works. What could be the problem?

PS. With this installation this is the first time I have an internet connection

---

### Post by ingo on 2005-12-28
how do you connect to the internet? ethernet, wlan? if so, what's the output of iwconfig? how comes windoze is having probs, too? can you get at your dhcp server and check the settings there?

just a load of questions, sorry :)

---

### Post by Vinze on 2005-12-28
I don't mind the questions, every try to help is great, so thanks a lot!

I connect via vlan. For the output of iwconfig I would have to reboot the computer, will do that in a sec. I have no problems at windows. I have no idea whatsoever how to get to the DCHP server.

Does that make it a bit clearer?

---

### Post by Vinze on 2005-12-28
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"belkin54g"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


^^^ Output of iwconfig

---

### Post by ingo on 2005-12-28
[QUOTE=Vinze]I connect via vlan. [/QUOTE]

I take it you have a wireless connection for a desktop computer. Your dhcp server would probably be your router/broadband modem but if windows works then the problem shouldn't lie there (I misunderstood the thing about trying six times).

Have you tried pinging the router with "ping 192.168.1.1"? Try it both with windows and with Ubuntu (for the latter you can get it to stop again with CTRL+C).

For further paths to go down there is a whole lot of stuff on networking with Ubuntu here [http://ubuntuguide.org/](http://ubuntuguide.org/)

Post your iwconfig output anyway if you've got it. BTW, getting an IP can take quite some time, sometimes up to five minutes!

---

### Post by Vinze on 2005-12-28
I already posted the output of iwconfig, maybe you missed it.

The output of the ping on Windoze:

C:\WINDOWS>ping 192.168.1.1

Pinging 192.168.1.1 with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 192.168.1.1:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum =  0ms, Average =  0ms

C:\WINDOWS>

For Linux I'd have to reboot again...

---

### Post by Vinze on 2005-12-28
Ping on Linux:

vincent@indo:~$ ping 192.168.1.1
connect: Network is unreachable

---

### Post by Vinze on 2005-12-28
If there's anyone else that can help, please do so soon, because Windoze is SO SLOW!

---

### Post by Vinze on 2005-12-29
I just installed the Windows driver with ndiswrapper, the install went all right, but I still have no internet, so the problem probably is not my driver. Oww..

---

### Post by stevea1210 on 2005-12-29
Is 192.168.1.1 the ip of your router?  I found a few things through google that stated the default ip of a belkin router may be 192.168.2.1.  Other companies use 192.168.0.1.

Also can you post the output of ifconfig.  You're iwconfig shows a connection to  a wireless network.  However, if you're wireless security isn't setup properly on ubuntu, you will not get an IP from the router.  Did you enter the correct wep/essid keys to connect to the router?

---

### Post by Vinze on 2005-12-29
[QUOTE=stevea1210]Is 192.168.1.1 the ip of your router?  I found a few things through google that stated the default ip of a belkin router may be 192.168.2.1.  Other companies use 192.168.0.1.

Also can you post the output of ifconfig.  You're iwconfig shows a connection to  a wireless network.  However, if you're wireless security isn't setup properly on ubuntu, you will not get an IP from the router.  Did you enter the correct wep/essid keys to connect to the router?[/QUOTE]

I don't know, it's just because ingo said I should do that that I did. But just to be sure, I also tried 192.168.2.1 and it didn't work.

I also posted the output of iwconfig before, it was

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11b+ ESSID:"belkin54g" Nickname:"acx100 v0.2.0pre8"
Mode:Auto Frequency:2.412 GHz Access Point: 00:00:00:00:00:00
Bit Rate=22 Mb/s Tx-Power=18 dBm Sensitivity=187/255
Retry min limit:7 RTS thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by stevea1210 on 2005-12-29
Actually, I wanted to see your i_f_config.  That wasn't a typo ;)

Since you have been rebooting into windows, and windows seems to have a connection, we can find your routers ip from there.  Reboot into windows, go to a command prompt and enter
```
ipconfig /all
```

Post that info here.  The default gateway should be the ip of your router.

---

### Post by Vinze on 2005-12-30
Subnet Mask . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . : 192.168.2.1
        DHCP Server . . . . . . . . : 192.168.2.1
        Primary WINS Server . . . . :
        Secondary WINS Server . . . :
        Lease Obtained. . . . . . . : 12 30 05 11:40:42
        Lease Expires . . . . . . . :

2 Ethernet adapter :

        Description . . . . . . . . : Microsoft TV Data Ada
        Physical Address. . . . . . : 00-00-00-00-00-00
        DHCP Enabled. . . . . . . . : No
        IP Address. . . . . . . . . : 4.0.0.0
        Subnet Mask . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . :
        Primary WINS Server . . . . :
        Secondary WINS Server . . . :
        Lease Obtained. . . . . . . :
        Lease Expires . . . . . . . :

3 Ethernet adapter :

        Description . . . . . . . . : PPP Adapter.
        Physical Address. . . . . . : 44-45-53-54-00-01
        DHCP Enabled. . . . . . . . : Yes
        IP Address. . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . :
        DHCP Server . . . . . . . . : 255.255.255.255
        Primary WINS Server . . . . :
        Secondary WINS Server . . . :
        Lease Obtained. . . . . . . :
        Lease Expires . . . . . . . :

4 Ethernet adapter :

        Description . . . . . . . . : PPP Adapter.
        Physical Address. . . . . . : 44-45-53-54-00-00
        DHCP Enabled. . . . . . . . : Yes
        IP Address. . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . :
        DHCP Server . . . . . . . . : 255.255.255.255
        Primary WINS Server . . . . :
        Secondary WINS Server . . . :
        Lease Obtained. . . . . . . :
        Lease Expires . . . . . . . :

I didn't know how I could select everything or scroll in the command prompt... Darn WinME...

---

### Post by stevea1210 on 2005-12-30
Those results let us know your routers ip is 192.168.2.1

> I also tried 192.168.2.1 and it didn't work.

ifconfig from linux should come back with an ip of 192.168.2.xxx, if all is good.  I don't think that is the case yet.  

What wireless security do you have on?  wep, wpa, ssid broadcast, mac filtering?
Did you enter the same settings for security as you put in for windows?

Also have you tried giving wlan0 a static ip?

---

### Post by encompass on 2005-12-30
I think you right.. my dad had an Belkin wireless router.  try pinging 192.168.2.1
heck... and try this too.
sudo dhclient
and then test your internet.
Othere problems might be your wireless card.  But I highly doubt it.  You could see if you can connect wth the cable.  like... that ethernet cable.  If you can connect to the ethernet then we know it is probably your wireless.

---

### Post by encompass on 2005-12-30
I have also seen problems with Wireless cards not working in linux, if the dhclient tries to connect first and then you try to dhclient to your wireless car.  Ubuntu may be trying to pull that one off too.

---

