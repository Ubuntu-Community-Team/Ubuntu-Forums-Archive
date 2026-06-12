---
title: "Wireless Driver/Wired Drive problems"
date: 2010-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by znikkisan on 2010-09-11
Hello, I am new to the site as a registered user, but have read some of the threads, and so far none of them are addressing quite what I need. I hope I am not stepping on any toes by doing this, please inform me if I am so I don't make the same mistake twice.

Anyway, about a year ago I bought a dell mini 9, and it came pre-loaded with the hardy heron edition of Ubuntu 8, and I had no problems with getting it connected to either the wireless or the wired connections.

In January my school switched its wireless to be protected by SecureW2, which wad not compatible with Linux, but thanks to a few of my friends, we figured out how to get our linux systems on the network (even though our school specifically stated it would not support linux, just mac and windows). One day I let my friend use my computer, and he accidentally started an update, but canceled it before it finished, leaving the dependency trees in shambles, and I had to wipe the computer, and I chose to install Ubuntu 10.04 netbook remix on it. When I did this it said it needed to download and install new wireless and wired drivers. But, it can't connect to the internet...so it can't get the drivers. (I am typing this from my other laptop, which has windows on it, which can connect to both wired and wireless). Is there a place that I can install these drivers using a windows laptop, onto a flash drive and then install it on the dell mini? (That is what I did to install 10.04 on my mini).

Thanks in advance!

Let me know if you need anymore information!

---

### Post by mörgæs on 2010-09-12
If you boot a live 9.10 and/or 10.04 with wired connection, can you access the internet?

---

### Post by znikkisan on 2010-09-12
No, wired connections are not working for me, either.

---

### Post by mörgæs on 2010-09-12
Is it also not working for 9.10?

Which network card do you use?

Have you enabled hardware drivers in the system -> administration menu?

---

### Post by znikkisan on 2010-09-12
network card: Broadcom BCM94312MCG

I tried to enable the drivers, but it said it couldn't find any drivers and that I needed to download/install them, I clicked on it to download/install them but it ended with an error message saying it couldn't connect.

---

### Post by coffeeaddict22 on 2010-09-13
Hi,
The standard install has drivers for most wired cards, so its a little unusual you can't get a wired connection.  
Can you open a terminal and type in ```
lshw -C network
``` and post the output back?  Also, there's a wiki page [for wireless here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"); it's pretty busy, but have a look at the first bit at least.

---

### Post by znikkisan on 2010-09-13
Hi! I figured out the issue: The university I attend hadn't gotten around to turning on the ports in the library yet, so once I went to their IT, they turned them on, and I was able to connect to the internet and download the appropriate drivers! So, there was nothing wrong with my ubuntu. Just idiots in the tech department.

But thank you so much for all your input and help!

---

