---
title: "Intel 4965AGN wireless won't connect to any network"
date: 2008-03-14
forum: Dell  Ubuntu Support
---

### Post by thorcik on 2008-03-14
I'm having this card installed in my m1330 notebook and the problem is that it is unable to connect to any wireless network, connection breaks while attempting to get the ip. I can see the networks around but can't access any of them. it's strange as I read it should work perfectly out-of-the-box.
does anyone have any ideas?

---

### Post by feistybill on 2008-03-19
I've been having problems with that damn 4965agn since I installed Linux on my current laptop. I spent months searching this forum, google, blogs, faqs, developers sites, repositories, etc. and the answer is... the 4965 is well supported by Windows only, while the Linux world don't seem to care much about it.
I haven't tried with ndiswrapper because I don't like the mess it makes (at packet-level), anyway... I chose Ubuntu because the 4965 seemed to work fine out of the box, but it would then suddenly stop working after a few reboots and I couldn't connect to any of the networks listed by network manager.
I tried updating the firmware and it seemed to work... for a while. I tried with the realtek patches that were suggested on this forum. I tried with the new iwlwifi, mac etc. I reinstalled Ubuntu each time, and also tried with WICD instead of network manager, tried with other distros, tried with the 8.04 alpha and the new kernel & modules... nothing! Even Fedora, Suse, Arch Linux and FreeBSD users are having random connection problems with the 4965. Looks like I'll have to stick with Windows until I win a lottery ticked and can afford a new laptop with a different wifi card :(

---

### Post by forceofnature on 2008-03-19
I havent had any problems with mine.  Is there something elso going on?  I know with my other PC after installing some applications I lost all wireless access.  I had to uninstall the network manager and then reinstall and that seemed to do the trick.

---

### Post by jespdj on 2008-03-20
> **feistybill said:**
> and the answer is... the 4965 is well supported by Windows only, while the Linux world don't seem to care much about it.
I don't believe that's true, Intel has an open source project and provides open source drivers for their wireless cards: [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

I've tested it on two laptops (Dell XPS M1330, Intel 4965 AGN, Ubuntu Gutsy 32-bit / Lenovo T61, Intel 4965 AGN, Ubuntu Hardy alpha 6 64-bit) and it works without problems on both (802.11n is not supported, however; connection speed is 802.11g (54 Mbit/s)).

I have read posts from people who had problems with the default network manager, and they use [wicd](http://wicd.sourceforge.net/) instead. I hope that's useful for you.

---

### Post by feistybill on 2008-03-20
EDIT: I tried Ubuntu 8.04 beta today. The wireless appears to work well out of the box, in fact I'm writing this from my Ubuntu :)

---

### Post by crosswalker21 on 2008-03-22
Hey everybody!

I'm experiencing a similar issue.  I have a Compaq Presario 2227US with a Broadcom bcm94306 wireless card inside.  I had everything working fine under Gutsy, but since I upgraded to Hardy beta 1, I can't connect to any networks.  I can see them, the light on my card is on, but when I go to connect, the little network icon in my panel just spins and spins and spins. . .you get the idea.

Any suggestions?
Also, what tools would I use to diagnose where the problem lies?

Thanks for any help!

---

### Post by Kernel Sanders on 2008-03-22
I too have this problem on my XPS M1330 :(

Everything seems to be working fine. I click on the toolbar icon, click on my correctly identified wireless network with great signal, and then the icon just spins and spins without connecting to my wireless network :(

---

### Post by jonnywombat on 2008-03-22
> **Kernel Sanders said:**
> I too have this problem on my XPS M1330 :(

Everything seems to be working fine. I click on the toolbar icon, click on my correctly identified wireless network with great signal, and then the icon just spins and spins without connecting to my wireless network :(

+1 on hardy 64bit with atheros 5006eg chipset running in ndiswrapper..

However I have found my old usb stick works just fine

---

### Post by GordonFreeman on 2008-03-22
I have a similar problem with my m1530 which also has a 4965agn: I can connect to my wireless router only when I'm clicking with left-click on the nm-applet an then my network (sometimes it finds the essid althouth it's hidden) or when I click "connect to another network" and in both cases I have to enter the key and in the second case I have to specify essid and encryption type.
In very rare cases the nm applet wants me to unlock the keyring and it connects automatically to my network, but most times I have to connect by myself.

But when I choose manual connect in the applet and specify essid, WEP key and everything it just tries to connect but never connects because it cannot find a dhcp server, the same occurs when I try to connect manually from the console using ifconfig, iwconfig, dhclient (following the howto in the networking subforum).

But when I let the nm applet establish the connection and only give it the information it queries for I can find the dhcp server using dhclient.

---

### Post by Nunslaughter on 2008-03-24
I had problems too with this card on my XPS m1710. Then I used Wicd instead of the standard network manager and it work a lot better, but still crappy. So I'm now using Gutsy with the Hardy kernel and the card works perfectly!!

[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

### Post by petoro on 2008-03-24
I think that the problem with 4965AGN has been solved with the last small update.

You can update the computer via cable.


Petoro

---

### Post by crosswalker21 on 2008-03-25
I can confirm that the last update to network manager (I assume it was this update) fixed wireless connectivity for the Broadcom (9)4306 card.  Huzzah for fast development!:)

**Update:**
Well, turns out it's only partialy fixed.  I can now successfully connect to my network, sometimes.  Restarting typically resolves connectivity issues, though not always.  Restarting into Windows xp (shudder) and then back into ubuntu seemed to help.  Another problem is that on my wireless G network (54 Mbps) I'm only getting a max of 2Mbps to my laptop.  I think it might be running in B mode, but I haven't confirmed that yet.  Also, network manager, and other network configs seem to think (intermittently) that the interface wlan0_rename (my wireless card) doesn't exist, though they'll usually connect.  Hopefully this will be fixed by Hardy's release date.

---

### Post by thorcik on 2008-03-26
as for me this update didn't accomplish anythig, wireless is still down, can't go past the IP configuration.

oh, and if I try to connect via terminal and dhclient, i get this:
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:7f:3b:3f
Sending on   LPF/wlan0/00:1d:e0:7f:3b:3f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

wmaster0 is something like an alias for wlan0

---

### Post by thorcik on 2008-04-02
ok, I fought a bit agaist it today and - hooray! - it works.
what I did was:
- removed all drivers (both the kernel modules and the driver from /lib/firmware) and installed the new ones from the intel website.
- installed wicd.
and all is fine.

---

### Post by atentik on 2008-05-27
How did you install wicd?

---

### Post by udrunk2? on 2008-06-19
I have been battling with this same problem for a few months(!!) on my m1330.  I dual boot and have been unable to use the wifi in ubuntu (Hardy) since adding security.  I am currently using Wicd 1.4.2 and it at least detects my SSID at rediculously close range, if I leave the room it won't detect.  But it still refuses to connect.  I have tried all the usual suspects and am completely frustrated.  I MUST use wpa2 where I live and cannot go back to unsecured which did work...

I have given up on using this 24/7 in the laptop and just wait for a miracle update from the magic underpants gnomes.

---

### Post by chifeatures on 2008-06-27
I'm also plagued by this 4965AGN issue on Hardy. I was using Hardy beta with no problems but since the final release I've had nothing but constant hair loss. I've now given up on wireless as much as it inconveniences me.

I do have various logs saved but simply do not have the experience to even diagnose what's going wrong let alone fix it. If whoever is interested in fixing it would like to reply I'd be overjoyed and willing bend over backwards to help.

Many thanks

---

### Post by chifeatures on 2008-06-30
I thought I'd add some attachments of dmesg output to the case. After all the reading I've done I'm not sure if anyone has actually nailed the cause? Plenty of outcry but not much dirt on what's causing this.

wlan0.txt - I recorded this output because my wireless was not working but as soon as I plugged in to the network through wired (eth0) wireless popped up. Was unable to repeat this so it's not a successful fix(/hack).

iwl4965 files - Some more dirt struggling to get the wireless going, shows output from startup and trying to figure things out.

I suppose this is more of a letter to Santa, I'm not sure if I'll get a reply but am still crossing my fingers! :)

---

### Post by poet_imp on 2008-07-17
I have a brand spanking new Thinkpad T61. Its very first boot was to the Kubuntu install CD. Everything works but wifi and I am getting frustrated. This is the only thread in the ubuntu forums that comes close to describing the problem I am having. 

I have the 4965agn card and can simply not connect to any networks. I see them but any attempt to connect fails. 

dmesg says:

[  274.659088] wlan0: RX deauthentication from 00:1a:e3:5c:4e:11 (reason=2)
[  274.659095] wlan0: deauthenticated
[  274.704465] wlan0: authenticate with AP 00:1a:e3:5c:4e:11
[  274.705614] wlan0: RX authentication from 00:1a:e3:5c:4e:11 (alg=0 transaction=2 status=0)
[  274.705623] wlan0: authenticated
[  274.705627] wlan0: associate with AP 00:1a:e3:5c:4e:11
[  274.713199] wlan0: associate with AP 00:1a:e3:5c:4e:11
[  274.714240] wlan0: RX deauthentication from 00:1a:e3:5c:4e:11 (reason=2)
[  274.714247] wlan0: deauthenticated

$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

$ uname -a
Linux paul-laptop 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686 GNU/Linux

$ lsmod | grep iw
iwl4965               109300  0
iwlwifi_mac80211      218724  1 iwl4965
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl4965

I have also:

sudo apt-get install linux-backports-modules-hardy-server

The last step above helped some. At least the status light on the laptop now works. 

Has anybody found a fix or workaround to this?

---

### Post by chifeatures on 2008-07-17
poet_imp,

We appear to be in the same boat. I haven't yet found any fix. The only difference I see is that you have installed linux-backports-modules-hardy-server as you appear to running the server edition.

Output of the same commands you ran:

lspci | grep Wireless
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

uname -a
Linux chi-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

lsmod | grep iw
iwl4965               105844  0 
iwlwifi_mac80211      219108  1 iwl4965
cfg80211               15112  1 iwlwifi_mac80211

---

### Post by rockhopper on 2008-07-18
Well, I can connect to AP without any trouble. However, the linux drivers for this card seem to have major problems in connecting to ad-hoc networks. I have tried the directions mentioned here: [http://www.debuntu.org/how-to-intel-wireless-4965-agn-with-ad-hoc-network-wep](http://www.debuntu.org/how-to-intel-wireless-4965-agn-with-ad-hoc-network-wep) ; but DHCP simply won't work!

---

### Post by poet_imp on 2008-07-18
I seem to be able to reliable connect to my simple home wireless. (old d-link). It is when I am here at work that I have the problem. I have 3 AP's in my vicinity. One uses PEAP, one uses MAC filtering and the third is open but requires a web login.

I have not tread the PEAP waters yet. Figured I would go for something simple first. It is the second network that I have been working so hard on. It simply refuses to connect. 

I have twice out of 20 times successfully connected to the open/web-login network.

I read somewhere that there is something different about the way the way the MAC address is assigned has changed on the 4965. I can't imagine why that would matter but it is something different.

I also saw where someone got past this by going to the command line and connecting manually. When he did he said that it only worked when he specified the frequency of the AP.

I spend more time at home than at work so I am not as desperate as I thought I was. I would still like to see a resolution. I am headed out to the mountains for a week so maybe, with luck this will all be solved by the time I get back. :)

---

