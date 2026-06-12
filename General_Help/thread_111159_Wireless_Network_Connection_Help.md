---
title: "Wireless Network Connection Help"
date: 2006-01-01
forum: General Help
---

### Post by marena23 on 2006-01-01
All,
I just installed Ubuntu and have been very happy with it as far as installation/setup goes however I am having trouble connecting to the Internet with my Linksys WUSB12 Wireless USB adapter.

If I type "ip address" I see the interface in the list but when I try to bring it up using "sudo ifconfig wlan0 up" it says "no such device" even though it's in the list.

When I bring up the network connection GUI wlan0 isn't in the interface list and I cannot figure out how to add it. Another interesting thing I noted was that when I use "ip address" it doesn't recognize the proper MAC for the wireless card (it shows 00:00:00:00:00:00)

Any thoughts on how to bring this device up?

---

### Post by Lambert on 2006-01-01
I believe this uses the linux-wlan-ng driver which is not installed by default but on the cd. put the cd back in and install linux-wlan-ng

[http://linux-wless.passys.nl/query_part.php?brandname=Linksys&zoek=brandname](http://linux-wless.passys.nl/query_part.php?brandname=Linksys&zoek=brandname)

not knowing your linux experience, if you're not sure how to install apps on linux there's a starter guide if you click the help icon (life preserver)

Once you install the driver package, then try to configure.

sudo ifconfig waln0 up just activates the device. There is more you need to do to configure the network.

See this link

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by marena23 on 2006-01-01
Thanks, I installed the package but I still cannot activate the device. I read the guide and it seems like I have all the pieces in place but still no good. I can see that my device is recognized as a USB device by the system but it still will not show up in the network-admin tool.

In the /etc/network/interfaces file it's mentioned but not sure if I need another entry.

Can you elaborate a bit when you say "Once you install the driver package, then try to configure."

Help is greatly appreciated.

Thanks,
Mike

---

### Post by marena23 on 2006-01-01
I am happy to say that I am writing this message from my Ubuntu machine. I read the instructions again and with the help of ndiswrapper it worked, thanks for your help!

---

### Post by Lambert on 2006-01-01
>  Can you elaborate a bit when you say "Once you install the driver package, then try to configure." 
Opening the network-admin gui highlighting the card and clicking properties and entering your network information. But you say the device isn't in that list. This means there is not a working driver if device is not listed.

Some devices work from this point some don't. See azz's post in this thread.

[http://ubuntuforums.org/showthread.php?t=106342]("http://ubuntuforums.org/showthread.php?t=106342")

You may need to also consider removing linux-wlan-ng driver and looking towards ndiswrapper with the windows drivers. If it comes to this there's a link in my signature.

---

