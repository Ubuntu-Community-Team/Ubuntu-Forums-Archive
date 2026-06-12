---
title: "Networking Issues"
date: 2006-03-28
forum: Desktop Environments
---

### Post by WoS on 2006-03-28
Greetings to all,

First of all I am sorry if there is another topic like this, but i couldn't find one like this.

So here is my problem:
I installed ubuntu i386 on my system just today and then i enabled all the available repositories (including universe and multiverse). Also i run pppoeconf to enable my Cable connection. And then i run the update. After downloading cca 80Mb of updates and installing them i proceeded with instaling mp3 support flash support and other "restricted" formats using this guide: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats). After that i also installed ATI drivers from their page using this guide: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI).
On the way I installed packages that were missing using apt-get.

Then i rebooted my system and first thing i saw is that NTP clock update failed which shouldn't as I set PPPoE connection to be enabled during boot time. After the system booted i opened Firefox but it wouldn't connect to any website. I tried running ifconfig but it wouldn't show any output. Then i opened System->Administration->Networking and noticed my network cards were "not-active"... So i actived then manualy, and then run pon dsl-provider to activate PPPoE. My internet connection then worked just fine. However after reboot all the problems are back and i have to do it all manualy. Also when i try to open System->Administration->Networking after enabling the network cards it takes a couple of minutes to open it. Same thing happens for a couple of other System->Administration items, while other start instantly.

Another issue is that i cannot reboot from my 2.6.12-10 kernel, everything just locks up when i try to do so, and o have to do a hardware reboot. When i boot to 2.6.12-9 kernel networking still remains with same issues but reboot works.

Thank you for your help in advance...

---

### Post by WoS on 2006-03-28
All problems solved :D
Network not starting was caused by pppoeconf missplacing one command in /etc/network/interfaces, and the slow opening of the admin modules by not activating te lo interface....
Not rebooting was coused by missconfogured ATI drivers which i fixed by adding new kernel headers and recompiling ...
Now i'm a new happy Ubuntu user :)
I hope it stays that way ;)

---

