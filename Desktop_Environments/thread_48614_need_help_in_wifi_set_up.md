---
title: "need help in wifi set up"
date: 2005-07-13
forum: Desktop Environments
---

### Post by mail2sona938 on 2005-07-13
I have a broadcom wifi card for which i managed to install the windows driver. It also switches on when linux boots up. I started KWifi and it detected the wireless network...but  I dont get a IP address assigned...so Im not able to ping to any website....ANY help is appretiated...

---

### Post by PokerFacePenguin on 2005-08-04
Its been a while for me and this proggie but i believe in kwifi you must enable  your profile.....only experience i had with using that program so far was in another distro.

It has icons that tell you what is happening with your card....

also, check out /etc/resolv.conf to see whether you have dhcp'd the network info by typing :

cat /etc/resolv.conf

hope this helps

---

### Post by PokerFacePenguin on 2005-08-05
[QUOTE=mail2sona938]I have a broadcom wifi card for which i managed to install the windows driver. It also switches on when linux boots up. I started KWifi and it detected the wireless network..(nice work guys!).but  I dont get a IP address assigned...so Im not able to ping to any website....ANY help is appretiated...[/QUOTE]


Ok, this made me curious....so I fired up my livecd kubuntu and it detected my wifi smc card after i activated the profilie....saw my wifi network, but no ip addy...

my quick fix was:

drop to konsole
sudo su
dhclient


you should now get an ip addy showing up in the console and in kwifi...

hope this helps

---

