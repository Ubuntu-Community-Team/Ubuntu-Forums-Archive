---
title: "Unable to get internet working in 6.06"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Ne0MindlesS on 2006-06-04
I connect on a home network with verizon dsl and a linksys, everything was connecting properly when i was using Ubuntu 5.10 then when i upgraded to 6.06 the connection simply stopped working.

ethernet card: 21x4x DEC-Tulip compatible 10/100 ethernet

when i run 'ifconfig' in terminal i get:

chris@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:08:A1:0A:96:5D
inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::208:a1ff:fe0a:965d/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:677 errors:10892 dropped:0 overruns:0 frame:0
TX packets:10 errors:6 dropped:0 overruns:0 carrier:6
collisions:0 txqueuelen:1000
RX bytes:95070 (92.8 KiB) TX bytes:828 (828.0 b)
Interrupt:177 Base address:0xd800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:222937 errors:0 dropped:0 overruns:0 frame:0
TX packets:222937 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:17450312 (16.6 MiB) TX bytes:17450312 (16.6 MiB)


but for some reason when i try to ping anything i get nothing back, 100% loss.

i have no f-ing clue how to fix + i am a *nix n00b =[
anyone have any idea?

---

### Post by adwait on 2006-06-04
What kind of connection do you have? Perhaps you have PPPoE which requires you to login? Can you ping IP addresses? If so, maybe your DNS settings aren't properly configured...Is your Ethernet card connected to a router which is in turn connected to the internet?

---

### Post by skinnygmg on 2006-06-04
same thing here.  no answeres yet

[http://www.ubuntuforums.org/showthread.php?t=188204](http://www.ubuntuforums.org/showthread.php?t=188204)

does anyone know what a loopback network connection/device is?

---

### Post by Ne0MindlesS on 2006-06-04
[QUOTE=adwait]What kind of connection do you have? Perhaps you have PPPoE which requires you to login? Can you ping IP addresses? If so, maybe your DNS settings aren't properly configured...Is your Ethernet card connected to a router which is in turn connected to the internet?[/QUOTE]

I have verizon dsl but i don't use PPPoE to login or at least never have before. no i can't ping any IP adresses (including those ON my home network). 

Yes, my ethernet card is wired to a router and the router is wired to my dsl modem. I never touched my DNS settings before so maybe thats it? if so i don't know what/how to configure them

---

### Post by adwait on 2006-06-04
a loopback device is the thing that makes the address localhost and 127.0.0.1 loop to you PC itself (atleast that's what I think it is....)

Anyway,well if u can't ping your home network, the problem isn't with the DNS. Check the network configuration in Ubuntu and see if you have assigned a static or dynamic address to the ethernet card. Does this setting match with the setting on the router?

---

### Post by RRS on 2006-06-04
> ethernet card: 21x4x DEC-Tulip compatible 10/100 ethernet

I believe one or both of these threads should help;
    [http://www.ubuntuforums.org/showthread.php?t=182618]("http://www.ubuntuforums.org/showthread.php?t=182618")
[http://www.ubuntuforums.org/showthread.php?t=186430]("http://www.ubuntuforums.org/showthread.php?t=186430")

---

### Post by sadjack on 2006-06-04
I would check
1. Default gateway is the IP address of your router
2. If wep is enabled that the correct key is used
3. The settings contained within /etc/network/interfaces, are they correct?

Hope you get it going

---

### Post by mehulved on 2006-06-05
Sorry for hijacking the thread but I am too having a problem getting my internet working in dapper.
I had breezy installed. I did a dist-upgrade.
After that I cannot conect to the internet nor can have any sound.
I have a always on cable connection. My settings were done and working fine in breezy but since installing dapper it's stopped working. My ethernet card is Via Rhine.
I cannot get to hear any sound too. I get error device not found. Though sound was working perfectly in breezy. 
I have onboard vinyl  AC'97 sound card.
During bootup I get stuck at following points
1) /etc/rcS.d/S40ifrename:line12:
/sbin/ifrename:no such file or directory
2)warning : error inserting genrtc device busy

---

### Post by deadgobby on 2006-06-05
[QUOTE=mehulved]Sorry for hijacking the thread but I am too having a problem getting my internet working in dapper.
I had breezy installed. I did a dist-upgrade.
After that I cannot conect to the internet nor can have any sound.
I have a always on cable connection. My settings were done and working fine in breezy but since installing dapper it's stopped working. My ethernet card is Via Rhine.
I cannot get to hear any sound too. I get error device not found. Though sound was working perfectly in breezy. 
I have onboard vinyl  AC'97 sound card.
During bootup I get stuck at following points
1) /etc/rcS.d/S40ifrename:line12:
/sbin/ifrename:no such file or directory
2)warning : error inserting genrtc device busy[/QUOTE]
  If you are running a cable modem try this simple thing.
Turn off you cable modem or unplug the modem and boot down your pc. Wait for at least a minute before turning on the cable modem. Let the modem do it testing. Leave the modem on and reboot your Drapper pc. It may be this simple process.
Gobby

---

### Post by mehulved on 2006-06-07
Thanks but I found the problem. It was that my kernel was not upgraded. I was using 2.6.12-10 kernel. It seems to have problem with Dapper. I updated to 2.5.15-23 and everything is working fine now except I still get 
/etc/rcS.d/S40 ifrename :line 12
/sbin/ifrename : no such file or directory.
I think ifrename has been outdated. That's what I think i found searching around in google. If so, how to remove this part?

---

