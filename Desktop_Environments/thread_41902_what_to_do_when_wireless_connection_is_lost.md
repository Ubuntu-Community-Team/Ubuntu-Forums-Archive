---
title: "what to do when wireless connection is lost?"
date: 2005-06-15
forum: Desktop Environments
---

### Post by boebel on 2005-06-15
Hi,
I'm often using my laptop at a site where I got a very bad connection (0-20%) and sometimes it loses connection. In fact it took me a reboots to write this text :? What should I do to re-establish my connection (and please don't say reboot :))?

I tried "sudo /etc/init.d/pcmcia restart" so as to restart my pcmcia card services but that doesn't work always (sometimes it gives "stopped ok started ok" without anything is happening)

It's not a major problem but it's still very annoying to reboot all the time, so any help is very much appreciated!

boebel

---

### Post by tread on 2005-06-15
sudo /etc/init.d/networking restart

---

### Post by boebel on 2005-06-15
Oh ok thank you, I will try this when it loses connection next time :)

cheers!

---

### Post by Gtaylor on 2005-06-15
You also might want to try something like this:
> 
ifconfig

Look to see the name of your wireless interface if you don't know it off the top of your head. This is usually something like wlan0 or eth1.
> 
sudo ifdown wlan0
sudo ifup wlan0

Assuming your wireless interface is wlan0. If not, replace it with the correct one. This is best suited if you aren't automatically starting the wireless interface at boot, which means it wouldn't be covered by the network script (I don't think).

---

### Post by imightbegiant on 2005-06-15
I've found that using 

```
$ sudo dhclient wlan0
``` 

works the best. This asks the DHCP server for a new ip address.  Where wlan0 can be any other interface like Gtaylor said.

---

### Post by boebel on 2005-06-15
> sudo ifdown wlan0
sudo ifup wlan0

thank you very much for your kind help everybody! The above solution works perfect so I'm gonna keep it at that :-)

Thanks again,
Boebel

---

