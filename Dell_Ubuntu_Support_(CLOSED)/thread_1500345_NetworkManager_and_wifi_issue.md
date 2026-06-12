---
title: "NetworkManager and wifi issue"
date: 2010-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by weijiajun on 2010-06-03
So, I am having an issue with the network manager that is installed on the system.  Here are the specs I have for my machine

E6500 
Intel Wifi (not broadcom)
Lucid x64

So when I start my machine about 70% of the time the wireless is down when the machine boots (the other 30% it is fine and everything works great).  

When the wireless is off (the light is off) I run the following command
  sudo ifconfig wlan0 up

This turns the light on for the Wifi, however the NetworkManager doesn't see it as being on still, it considers it enabled.  Then if I try to kill NetworkManager (which autostarts after) it actually turns off the wlan0 as soon as it starts up.  

I don't know if I have a problem with the NetworkManager or if the issue resides in the card and that the LED doesn't mean anything, but any suggestions people have would be greatly appreciated.

One more thing, when I turn off the wifi using the physical off button it does turn it off, but when I turn it back on, the wifi doesn't come back on I have to run the ifconfig again.

---

### Post by weijiajun on 2010-06-03
Well I was able to get it to work again by removing the network manager (purging the package) then manually setting up the connection (found in this awesome article [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)) which I then downloaded from the internet, I didn't use the copy that came on the CD.  

I still feel it might fail again (since any problem that goes away by itself will generally come back by itself) but at least my wireless is working right now. \\:D/

---

