---
title: "Wireless feedback"
date: 2007-10-12
forum: Dell  Ubuntu Support
---

### Post by factor2 on 2007-10-12
I bought a Dell Inspiron 1420 with Feisty pre-installed. The thing works great in most ways, but the wireless configuration has driven me batty. If I'm on a network without WEP or WPA I can connect easily. But using WEP is arduous. What I have to do everytime I turn on the machine:
1. open network manager and uncheck my wireless
2. open terminal, and type the WEP key via iwconfig
3. recheck the wireless connection in the network manager.

Most of the time doing this little dance works, but sometimes it doesn't. At times if I type ifconfig it displays some foreign IP for my wireless card (which I assume to be the IP out of the box). The laptop comes with the Intel 3945 WLAN (802.11a/g) Mini Card. 

Wireless should always work! Was the card ever tested with Network Manager? All over the internet there are forums detailing this problem, most users have dropped Network Manager altogether. 

Little irksome things like this will always keep Linux in the domain of power users only.

---

### Post by neptho on 2007-10-13
Are you, by any chance, using LinkSys gear?

My 3945 works fine with everything BUT my new LinkSys WRT4GL.  It's always a hazard; sometimes I need to ifdown my interface and let it set for 3 seconds, or I'll get a load of messages about retrans.

The only fix I've found is to use my old AT&T router rather than the LinkSys, which is hardly optimal.

I hope that this problem goes away when the open source version of the ipw3945 matures.

---

### Post by sstusick on 2007-10-13
Have you tried Knetworkmanager? I find that it is superior to the default gnome network manager.

---

