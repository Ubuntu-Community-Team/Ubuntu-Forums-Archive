---
title: "Wireless connection does not AUTO CONNECT"
date: 2010-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BrownHorse on 2010-05-02
I just installed Ubuntu 10.04 yesterday. Downloaded the driver for my built in wireless card and set up the wireless connection with no problems. I am able to connect wirelessly to WAN without any issues however, each time I reboot the laptop, it does not automatically connect to my home wireless connect (SSID). I do have the flag "Connect Automatically" turned ON under Network connection. I removed the connected, re added it twice and still same results

Laptop: Dell Inspiron 1525
Problem Description: Wireless connection does not auto connect when Laptop is turned on

Please help!!!

Thanks!

---

### Post by pxwebdev on 2010-05-04
From my experience what I would recommend you do is delete that connection and just recreate it again making sure that when you do check the auto connect box at the time of creation.

---

### Post by BrownHorse on 2010-05-04
> **pxwebdev said:**
> From my experience what I would recommend you do is delete that connection and just recreate it again making sure that when you do check the auto connect box at the time of creation.

I did that three times. still same results. I am wondering if its because my SSID is hidden (Not broadcasting). I will try to enable SSID broadcast on my access point and see if that fixes. I just thought about it :) I guess I am more awake today

---

### Post by Fastjack77 on 2010-06-28
Hi,

I have the same problem with this laptop (coincidence?), with a non broadcasted network.

Let me know if you find a solution.

Thanks,

---

### Post by Jonny Two Shoes on 2010-06-30
My SSID is hidden and also does not autoconnect so it's probably that :)

---

### Post by Nergar on 2010-07-10
having same problem here, same laptop. but my network DOES broadcast it's SSID

Anyone knows any fix??

---

### Post by finalcut on 2010-07-11
i had the same problem about a year ago when i use to use ubuntu a lot it was the 8.04 distro. i cant remember what i did to fix the issue

---

### Post by mikewhatever on 2010-07-11
Setting up a static IP might help, as well as providing BSSID, which is the router's MAC address. In my experience, when the SSID is hidden, it some times takes up to a minute or two to autoconnect.

---

### Post by Fastjack77 on 2010-07-12
_I found a solution!_ (tested on two different laptops, Xubuntu 10.04 i386 and Ubuntu 10.04 AMD64 Desktop edition, NetworkManager Applet 0.8 )

1. Right-click on the NetworkManager icon.
2. Click on "Edit Connections..."
3. Select the "Wireless" tab.
4. In the table, select your connection and click "Edit".
*5. UNCHECK "Available to all users" and apply changes.

This solved it for me. Just in case, here is more details about my connection:

- Using Manual IPv4 settings, with gateway as DNS server.
- Ignoring IPv6.
- "Connect automatically" checked.
- "Available to all users" unchecked.

Unfortunately, I guess not "all users" will have the connection available.

Hope this helps.

---

### Post by sihtworth on 2010-08-08
> **Fastjack77 said:**
> _I found a solution!_ (tested on two different laptops, Xubuntu 10.04 i386 and Ubuntu 10.04 AMD64 Desktop edition, NetworkManager Applet 0.8 )

1. Right-click on the NetworkManager icon.
2. Click on "Edit Connections..."
3. Select the "Wireless" tab.
4. In the table, select your connection and click "Edit".
*5. UNCHECK "Available to all users" and apply changes.

This solved it for me. Just in case, here is more details about my connection:

- Using Manual IPv4 settings, with gateway as DNS server.
- Ignoring IPv6.
- "Connect automatically" checked.
- "Available to all users" unchecked.

Unfortunately, I guess not "all users" will have the connection available.

Hope this helps.
I've tried all this already and still not got it to connect automatically. Dang and double dang.

---

### Post by fubar65 on 2010-08-15
Thanks Fastjack77, that worked perfectly for me :D

as soon as I get my print server figured out I will be installing linux on the wifes laptop too.


this place is a great resource, I am very happy I found it!

Cheers.

---

### Post by triwave on 2010-08-27
Actually I've tried those tricks and it didn't resolve my issue with a hidden WPA2 enterprise network.

I think I know what did however.

There is a network nearby that is not hidden that was automatically added to my network list (probably connected to it at some point in time...)

If I connect to my hidden network and it disconnects it never reconnects. After removing the network with a visible SSID that isn't used (but is near enough to get a signal and was in my list of networks) it now re-connects to my hidden (and desired) network.

I guess even though the desired network is much stronger than the undesired the NM selected the weak but visible signal.

I removed the entry from the network list and my problem was solved. (for now anyway...)

---

