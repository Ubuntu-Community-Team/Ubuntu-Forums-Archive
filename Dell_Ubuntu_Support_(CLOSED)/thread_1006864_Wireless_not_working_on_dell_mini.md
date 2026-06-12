---
title: "Wireless not working on dell mini"
date: 2008-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by reader68 on 2008-12-09
Hi,I am really hoping someone can help me. 

I have just recently purhcased a Dell mini 9 with Ubuntu 8.04.1 preinstalled. After downloading the correct driver and running ndiswrapper the pc now sees my wireless network at home however it will only connect if I disable the WEP key on my Linksys WRT150N router. Does anyone have any ideas on getting it to connect to my secured network? I have tried changing the channel on my router as it was set to Auto but it is still not working.


Any help would be greatly appreciated.

---

### Post by anjilslaire on 2008-12-09
Uh, the Dell Linux install shouldn't ndiswrapper or anything to have eh wierless running. In fact, even if you install vanilla ubuntu, the wireless simply works after getting the latest updates.

BTW, you should really use wpa instead of wep, its much more secure..

---

### Post by pytheas22 on 2008-12-09
Yes, as the above poster says, Dell really should have configured the wireless for you, or so I would have thought.  Are you sure it wasn't working out-of-the-box?

Anyway, it's possible that Network Manager, the default connection manager in Ubuntu, doesn't like your router for some reason--especially if you're using a weird WEP key (i.e. an ASCII key instead of normal HEX).  In that case, it may help to install wicd by typing:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch wicd from the Applications>Internet menu.  Do you have better luck connecting to your encrypted network then?

N.B.: installing wicd will require that you install Network Manager because they conflict.  If you want NM back later for any reason, just type 'sudo apt-get install network-manager-gnome'.

If wicd doesn't help, we can look at some other things if you post the output of:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
lspci -nn
```

But really on a machine with Ubuntu preinstalled, I'd be sad if it came to hacking in the command line to get the wireless working!

---

### Post by reader68 on 2008-12-10
If I was supposed to do something in order for Ubuntu to see my network then it could have been working. But if it was supposed to see my network with any intervention on my part then I would have to say that it wasn't working.


Tried to install wicd and I get the following error.

[http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz) 404 Not Found.

> **pytheas22 said:**
> Yes, as the above poster says, Dell really should have configured the wireless for you, or so I would have thought.  Are you sure it wasn't working out-of-the-box?
Anyway, it's possible that Network Manager, the default connection manager in Ubuntu, doesn't like your router for some reason--especially if you're using a weird WEP key (i.e. an ASCII key instead of normal HEX).  In that case, it may help to install wicd by typing:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch wicd from the Applications>Internet menu.  Do you have better luck connecting to your encrypted network then?

N.B.: installing wicd will require that you install Network Manager because they conflict.  If you want NM back later for any reason, just type 'sudo apt-get install network-manager-gnome'.
If wicd doesn't help, we can look at some other things if you post the output of:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
lspci -nn
```

But really on a machine with Ubuntu preinstalled, I'd be sad if it came to hacking in the command line to get the wireless working!

---

### Post by pytheas22 on 2008-12-11
> 
Tried to install wicd and I get the following error.

[http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz) 404 Not Found.

Were you plugged into the Internet first?  You would need to be online via ethernet in order to download wicd using those commands.  But if you have no way of getting online without wireless, you can still install wicd with some extra work, so let us know.

It would also be helpful to see the output of:
```

lshw -C Network
sudo iwlist scan
lspci -nn
```

in order to figure out what's really going on.

---

### Post by jsonder on 2008-12-11
I have avoided installing wicd because the binaries are for an i386 machine not an lpia machine.  The mini has a "low power intel architecture" designation.

There's about 76 pages in the mini forum topic:

[http://ubuntuforums.org/showthread.php?t=910487&page=1](http://ubuntuforums.org/showthread.php?t=910487&page=1)

There are several discussions about the wireless card.  Mine found the WAP running WPA passphrase limitations and once the passphrase was entered it was an automatic connection.  Most people have been tickled that Dell's massaging eliminated the lost passphrase problem that the 8.04 Ubuntu network manager had (also why I use wicd on my Inspiron 1505 with 8.04-1).

---

### Post by pytheas22 on 2008-12-11
> I have avoided installing wicd because the binaries are for an i386 machine not an lpia machine. The mini has a "low power intel architecture" designation.

This is getting off-topic, but wicd is really just a Python script, so it shouldn't really matter what kind of machine architecture you use as long as you have Python installed (and every Ubuntu system should have Python by default).  Or am I wrong?

---

### Post by Cookster248 on 2008-12-24
I have the same router.  I had a similiar problem. I just changed the router IP (mine was 192.168.1.1) to 192.168.2.1 I had to renew the IP on my Vista machine in the cmd promt using ipconfig /release   then ipconfig/ renew. Found this solution on a guys blog.

---

