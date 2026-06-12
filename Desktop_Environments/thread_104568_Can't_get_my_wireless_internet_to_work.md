---
title: "Can't get my wireless internet to work"
date: 2005-12-16
forum: Desktop Environments
---

### Post by elreteipos on 2005-12-16
Hi everybody,

I have a WLAN and I managed to install the necessary drivers for my WLAN reciever stick (chipset ZyDAS-1201) today. I think I got everything to work, but still I can't connect to the internet. What could be the cause of this?

[http://img220.imageshack.us/img220/8182/screen15jf.png](http://img220.imageshack.us/img220/8182/screen15jf.png)
[http://img220.imageshack.us/img220/3332/screen22sq.png](http://img220.imageshack.us/img220/3332/screen22sq.png)
[http://img230.imageshack.us/img230/143/screen36sj.png](http://img230.imageshack.us/img230/143/screen36sj.png)
[http://img230.imageshack.us/img230/5319/screen41xz.png](http://img230.imageshack.us/img230/5319/screen41xz.png)

Greetings and thanks in advance,

Pieter

---

### Post by Mozzer on 2005-12-16
If you can connect to your router but not external websites then the chances are Ubuntu isn't resolving properly.

Go into terminal and do

```
sudo gedit /etc/resolv.conf
```

In this file add the line

nameserver 192.168.0.1

where the IP address is that of your router or default gateway.

Hope that helps.

---

### Post by elreteipos on 2005-12-17
Are you sure it is /etc/resolv.conf? That file is empty here, but anyway, it didn't work. (I didn't reboot after that, is that necesary?)

---

### Post by anil_robo on 2005-12-17
First, check if your network is of static IP type or DHCP type. My wireless network gives me internet only when it's set to DHCP.

Second, check your router documentation, or call your router company to determine if the router address is  192.168.0.1 or something else. In my case, it's a 2wire router with default router address as 192.168.1.254. It took me a long time to realize that it could be a nonstandard router IP causing problems! :)

---

### Post by Mozzer on 2005-12-17
[QUOTE=elreteipos]Are you sure it is /etc/resolv.conf? That file is empty here, but anyway, it didn't work. (I didn't reboot after that, is that necesary?)[/QUOTE]
Yeah, it was the same for me; the file was empty before I added the nameserver bit. And a reboot shouldn't be necessary.

To quickly test if it's working, have the Terminal window open and type in

```
host google.co.uk
```

If it does nothing then it's still not resolving. However if you are successful it should give you this result more or less straight away:

```
mozzer@ubuntu:~$ host google.co.uk
google.co.uk has address 216.239.57.104
google.co.uk has address 216.239.59.104
google.co.uk has address 216.239.39.104
google.co.uk mail is handled by 30 smtp3.google.com.
google.co.uk mail is handled by 10 smtp1.google.com.
google.co.uk mail is handled by 20 smtp2.google.com.

```

Good luck.

---

### Post by elreteipos on 2005-12-18
My network can handle both DHCP and static, but for my computer I've chosen a static address. (as you can see [here]("http://img220.imageshack.us/img220/8182/screen15jf.png"), it's 192.168.1.199)

I used Firefox to check my router IP and it is 192.168.1.1, as I thought before.

---

### Post by elreteipos on 2005-12-19
That's strange, I can't boot Ubuntu anymore. To be precise, X11 is not working here anymore. I can hear the bootup sound of the graphical login screen, but my screen doesn't display the graphical interface anymore. I still have access to the console.

What do I have to do now?

---

### Post by elreteipos on 2005-12-21
Anybody?

---

