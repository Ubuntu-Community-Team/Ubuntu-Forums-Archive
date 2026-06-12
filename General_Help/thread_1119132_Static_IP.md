---
title: "Static IP"
date: 2009-04-07
forum: General Help
---

### Post by pylon42 on 2009-04-07
I've seen a lot of tutorials on how to switch to a static IP. They're all pretty much the same - things like this:
[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

They all work for me just fine after I restart my networ. However, if I have to reboot I lose network connectivity. Any ideas why this might happen? Any easy ways to switch to a static IP permanently?

---

### Post by lisati on 2009-04-07
> **pylon42 said:**
> I've seen a lot of tutorials on how to switch to a static IP. They're all pretty much the same - things like this:
[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

They all work for me just fine after I restart my networ. However, if I have to reboot I lose network connectivity. Any ideas why this might happen? Any easy ways to switch to a static IP permanently?

My experience of IP is limited to setting my router to use DHCP, and setting static IPs on the router for my own computers. So far it has worked like a charm.

---

### Post by 3Miro on 2009-04-07
Gnome network manager and KDE network manager have some trouble with the static IP. For Gnome I managed to do it after uninstalling the NM and doing it manually. For KDE I just installed WICD:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by spiderbatdad on 2009-04-07
From what is saw on the link you provided...you might comment out auto eth0 like so: #auto eth0.
Also it is usually good to assign and address outside the range of dhcp addresses that your router uses. So, if your router starts assigning addresses at 100 and goes to 150, you might choose 99 if nothing else is using 99. So your inet would be 192.168.1.99, for example.

---

### Post by GeeZor on 2009-04-07
What you are looking for is a configuration in /etc/network/interfaces

in that file you can configure your network.. 
mine looks like this:
```

auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp


iface ath0 inet static
address 192.168.2.210
netmask 255.255.255.0
wireless-essid gbb
gateway 192.168.2.200
pre-up wpa_supplicant -B -Dwext -iath0 -c/etc/wpa_supplicant.conf
#pre-up wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
iwconfig ath0 rate 48M
mount -a

auto wlan0
#iface wlan0 inet dhcp

auto ath0

#auto eth0


```

i use ath0 (wifi with wpa) but you should google around for other configurations that best suite your situation (probably eth0)..

this file gets loaded each time your machine boots...

good luck

---

### Post by coffeecat on 2009-04-07
You don't need to use the command line. And, besides, that page is from 2006. A comment there from earlier this year says that it caused network manager to disappear. Depending on your version of Ubuntu, you can use the GUI. In Jaunty I right-click on the network-manager applet and choose 'Edit connection' and it's pretty plain sailing thereafter.

In Hardy, you go to System > Adminstration > and I can't remember what next but it's something to do with Networking. It's an easy to use GUI utility. Intrepid is either similar to Hardy or Jaunty, I can't remember which. So, which version are you using? Hardy, Intrepid or Jaunty?

And if you're using an earlier version, it's about time you reinstalled. :p

---

### Post by 3Miro on 2009-04-07
> **coffeecat said:**
> You don't need to use the command line. And, besides, that page is from 2006. A comment there from earlier this year says that it caused network manager to disappear. Depending on your version of Ubuntu, you can use the GUI. In Jaunty I right-click on the network-manager applet and choose 'Edit connection' and it's pretty plain sailing thereafter.

In Hardy, you go to System > Adminstration > and I can't remember what next but it's something to do with Networking. It's an easy to use GUI utility. Intrepid is either similar to Hardy or Jaunty, I can't remember which. So, which version are you using? Hardy, Intrepid or Jaunty?

And if you're using an earlier version, it's about time you reinstalled. :p

That is exactly what I was trying in 8.10 Ubuntu and Kubuntu and both work until you reboot. In KDE it is listed as a bug and for Gnome there is a way but it is no obvious (something about creating a new connection without deleting the default one, but I have never tried it).

---

### Post by coffeecat on 2009-04-07
> **3Miro said:**
> That is exactly what I was trying in 8.10 Ubuntu and Kubuntu and both work until you reboot. In KDE it is listed as a bug and for Gnome there is a way but it is no obvious (something about creating a new connection without deleting the default one, but I have never tried it).

OK, thanks. I wasn't aware of that bug. I'll try setting a static IP in Jaunty and come back shortly after a reboot.

---

### Post by bodhi.zazen on 2009-04-07
I too find network manage is very nice when it works, it does have bugs however.

I agree the easiest way for me to set a static IP address is to disable network manager (you do not need to remove it) and edit the config file directly.

Take care, however, to back up you working confg file as it will be over written by network manager ;)

---

### Post by coffeecat on 2009-04-07
> **3Miro said:**
> That is exactly what I was trying in 8.10 Ubuntu and Kubuntu and both work until you reboot. In KDE it is listed as a bug and for Gnome there is a way but it is no obvious (something about creating a new connection without deleting the default one, but I have never tried it).

> **coffeecat said:**
> OK, thanks. I wasn't aware of that bug. I'll try setting a static IP in Jaunty and come back shortly after a reboot.

Well, that didn't take long. That's what I like about Jaunty - a nice swift bootup. :p

Anyway, I've set a static IP using n-m applet and it has survived a reboot. This posting is the proof of the pudding.

**pylon42**, you clearly need Jaunty. It's a doddle. Just a right-click on network manager, etc. If you don't want to be running the Beta/RC, you've not long to wait to the final release.

---

### Post by bodhi.zazen on 2009-04-07
Ah, glad to see it is fixed in 9.04, /me wonders about a back port ???

---

### Post by mb_webguy on 2009-04-07
It works for me in Intrepid.  I just went to Network Configuration (via the Network Manager applet or through the menu), edited my current network configuration, and on the IPv4 Settings tab entered the IP of my router for the Gateway and DNS Server, 255.255.255.0 for the Netmask, and whatever I wanted within the acceptable range of IPs for the computer's static IP (e.g. 192.168.2.10, in my case).

Actually, I'm doing this with a wireless connection, which should obviously be more problematic than a wired connection.  I don't have any problem at all either on a reboot or reconnect.

---

### Post by pylon42 on 2009-04-07
Very odd. I've tried the gui (gnome) as well with the same results. Works fine until I reboot.

I'm running 8.10 at the moment, but I'll bump up to Jaunty tomorrow and let you know if the problem goes away.

---

### Post by pylon42 on 2009-04-08
Installed Jaunty.

edited /etc/network/interfaces
/etc/init.d/networking restart

Everything worked perfectly. 
Rebooted, no network.

I tried editing eth0 using the gnome gui interface (The same as I had done 50 times with no success in Intrepid) and it worked like a charm, even after rebooting - woot!

So there we have it. I look forward to 9.10.

---

