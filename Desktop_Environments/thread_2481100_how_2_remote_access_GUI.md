---
title: "how 2 remote access GUI"
date: 2022-11-19
forum: Desktop Environments
---

### Post by ihadtomakeanamelikethis on 2022-11-19
Goal : Ubuntu box setup for remote access of my network / servers. The site is un-manned.

I have 3 internet providers all bonded to one router for failover / speed. The Ubuntu box will be directly connected to one of the ISP's, via NAT. And have a 2nd LAN to inside network. ( Or via a  4G modem )

If a server needs "worked on", I want to remote (VNC, RDP, or some other remote tool that uses GUI), then RDP to a server. Or remote to ubuntu box and access web interfaces of equipment. 

For this to work it needs to be GUI. I can access via SSH. However EVERY other remote access I've tried fails or has issues. 

Built in VNC, just shows a black screen.
Built in RDP, all client RDPs crash, error or just shows light blue background
3rd party VNC software, mostly fails to connect, or shows empty screen
WEB based remote software just shows black screens with some text at top. 

System has a static IP. Firewall is off, and I also tried opening the ports (3389 for example). I have tried most every remote software or built in options I can find. I have wiped and started fresh many times, including changing hard drives for clean base setup.  


I eventually got a VNC solution to work, but compared to RDP, VNC is not real good. Laggy, low res, slow to react. But "fine" at least I can access it. But its very random and glitchy, need to do a rain dance when trying to access. Turns out the password just randomly changes?  At first I was changing the auto generated pass with mine. But, it would eventually default to some random pass. " FINE",, I'll just document the auto generated password.. Only to discover that auto generated remote password constantly changes!? It needs to be a static password, otherwise I'll need another system to remote to the Ubuntu system so I can get the password, then log directly to the ubuntu using the constantly changing password. 


So, can one actually RDP or remote access via GUI?

---

### Post by TheFu on 2022-11-19
For remote access into a server, use IPMI.  If that isn't possible, you'll need a pikvm device.
[https://pikvm.org/](https://pikvm.org/)   While you can build your own from parts, the hassles and complexity make it worth the $25 extra getting a pre-built version costs.  Of course, if you already have a r-Pi v4 that can be purposed for this, the hassle and reuse could be worth it.

The pikvm and IPMI methods allow you to reboot a system and modify the BIOS remotely.  All other methods fail at this, critical, aspect.

But if you don't have $250 for hardware, to get secure remote access using VNC or RDP, a full VPN/ssh tunnel is needed.  But if the remote system has NAT that cannot be given a tiny hole through, then you are limited.  Of course, no software-only remote access method allows BIOS access.  This is critical for professional environments.  Places that I worked would ensure remote access to the boot-console was available to all servers.  Just 1 last minute trip every 5 yrs by any admin paid for the needed device, so it was company policy.

There are a number of peer-to-peer VPNs.  TINC, Nebula, and a few others work, but they aren't great for performance.

If you are becoming a server admin, forget the GUI. Learn to do things over ssh and only ssh.  Tools like 'webmin' are usually worse than the problem and open the system for remote attack.

So, I know you aren't going to listen to all the advice above.  For my home, I don't either, but I do use ssh for server admin.  OTOH, sometimes a remote GUI is good, like when I'm traveling in not-so-friendly countries and don't want to bring any sensitive data with me.  For those situations, I'll have a flash-based Linux with 'ssh' and 'x2go' clients.  x2go uses the NX protocol which is a combination of ssh for network security and a highly optimized/compressed VNC implementation.  ssh-keys work with x2go. From a Linux workstation, the ~/.ssh/ configs are honored fully.  The NX-VNC is 2-3x faster than normal VNC.  New users say the difference is like comparing "night to day".  I've used x2go from 5 continents, sometimes very remote connections at ISDN speeds.  For those, I just configure the connection to use smaller images (4k) and tell the x2go client that the connection is 1-level less than predicted.  This impacts the way that x2go connection so it is responsive through the available bandwidth.

There is 1 downside.  x2go doesn't work with DEs that demand direct access to the GPU. So, KDE Plasma and GNome 3+ don't work.  OTOH, xfce, Mate, and pure-WM-only setups work fantastic.  They are like being on the same subnet for almost all uses.  Of course, don't expect to have perfectly streamed video playback.  OTOH, email, admin stuff, editing office documents all work fine.

If you don't want F/LOSS x2go, there is a commercial product from NoMachine that has been proprietary and updated so that it is incompatible with all other NX implementations.  But some businesses like paid software/support.

But if you really need this, just get a pikvm device.  Seriously. That's the best answer to remote server admin needs, short of getting a Unix remote access terminal server that does console serial connections to 8-24 Unix servers for $2500+.

---

### Post by ActionParsnip on 2022-11-21
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)
For accessing over the Web, use the SSH tunnel

---

