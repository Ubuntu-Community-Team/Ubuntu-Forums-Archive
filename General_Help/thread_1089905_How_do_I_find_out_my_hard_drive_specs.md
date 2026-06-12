---
title: "How do I find out my hard drive specs?"
date: 2009-03-07
forum: General Help
---

### Post by tanha on 2009-03-07
Specifically, I would like to know if it is 1.5 Gbps or 3 Gbps? Is there a command or program that will tell me this? 

Thanks.

---

### Post by Slim Odds on 2009-03-07
google the model number

---

### Post by tanha on 2009-03-07
> **Slim Odds said:**
> google the model number

Yes, thank you. I know what it is based on the model number and all that. I'm actually trying to find out what the OS reports it to be...through a command or application I guess.

---

### Post by bapoumba on 2009-03-07
I use gnome-device-manager (in universe).

---

### Post by tanha on 2009-03-07
> **bapoumba said:**
> I use gnome-device-manager (in universe).

Thank you. That is indeed an interesting program; a lot of info. I didn't however see the info for which I was looking. Do you know if it specifies whether it's 1.5 or 3.0 Gb/s in there somewhere, I couldn't find it.

---

### Post by bapoumba on 2009-03-07
> **tanha said:**
> Thank you. That is indeed an interesting program; a lot of info. I didn't however see the info for which I was looking. Do you know if it specifies whether it's 1.5 or 3.0 Gb/s in there somewhere, I couldn't find it.

```
sudo hdparm -I /dev/sda | grep SATA
```

```
bapoumba@SonyBlue:~$ sudo hdparm -I /dev/sda | grep SATA
	   *	SATA-I signaling speed (1.5Gb/s)
```
Assuming you have a SATA drive on /dev/sda ;)

---

### Post by tanha on 2009-03-07
> **bapoumba said:**
> ```
sudo hdparm -I /dev/sda | grep SATA
```
Assuming you have a SATA drive on /dev/sda ;)

That's awesome, thank you! The only trouble is, the features, enabled support show both: SATA-I signaling speed (1.5Gb/s) and SATA-II signaling speed (3.0Gb/s). How can I tell which one it's using?

---

### Post by bapoumba on 2009-03-07
> **tanha said:**
> That's awesome, thank you! The only trouble is, the features, enabled support show both: SATA-I signaling speed (1.5Gb/s) and SATA-II signaling speed (3.0Gb/s). How can I tell which one it's using?
I do not know, I'll have to search further. Please see my edit in the post above, not sure I can test :)

---

### Post by bapoumba on 2009-03-07
[http://www.cyberciti.biz/tips/how-fast-is-linux-sata-hard-disk.html](http://www.cyberciti.biz/tips/how-fast-is-linux-sata-hard-disk.html)
From this link, both can be used if BIOS/Motherboard have support.

I've been looking but did not find anything useful.
What are you trying to do exactly?

---

### Post by tanha on 2009-03-07
> **bapoumba said:**
> [http://www.cyberciti.biz/tips/how-fast-is-linux-sata-hard-disk.html](http://www.cyberciti.biz/tips/how-fast-is-linux-sata-hard-disk.html)
From this link, both can be used if BIOS/Motherboard have support.

I've been looking but did not find anything useful.
What are you trying to do exactly?

Well, long story short, I just installed a new HDD on my macbook. It's a 3Gb/s drive, SATA II. There are three jumper settings, default (no jumpers used), reduced power spinup, and spread spectrum clocking. I'm using default/ no jumpers. My controller is a ICH8-M AHCI and intel's site says that this controller supports 3Gb/s. The problem is that os x 10.5 reports 1.5Gb/s, and I don't know why. So, I was trying to see what ubuntu says it is, but didn't know how. That's where your help came in really handy.
Edit: 
hdparm timing cached reads is about 3080MB in 2.00 seconds = 1541.07 MB/sec
hdparm timing buffered disk reads is about 164 MB in 3.02 seconds = 54.36 MB/sec

Why would the drive be restricted to 1.5Gb/s?

---

### Post by dcstar on 2009-03-07
> **tanha said:**
> Well, long story short, I just installed a new HDD on my macbook. It's a 3Gb/s drive, SATA II. There are three jumper settings, default (no jumpers used), reduced power spinup, and spread spectrum clocking. I'm using default/ no jumpers. My controller is a ICH8-M AHCI and intel's site says that this controller supports 3Gb/s. The problem is that os x 10.5 reports 1.5Gb/s, and I don't know why. So, I was trying to see what ubuntu says it is, but didn't know how. That's where your help came in really handy.
Edit: 
hdparm timing cached reads is about 3080MB in 2.00 seconds = 1541.07 MB/sec
hdparm timing buffered disk reads is about 164 MB in 3.02 seconds = 54.36 MB/sec

Why would the drive be restricted to 1.5Gb/s?

The SATA connection speed is not the bottleneck that will affect your disk performance, the physical limitations of the medium will far outweigh any trivial difference between 1.5 or 3Gb/s on the pipe that plugs into the drive.

You can also use an industrial 100 Amp power cable to plug your PC into the wall, it isn't going to make your PC work any faster.

---

### Post by smooch101 on 2009-03-07
in a file browser right click a file then it tells you how much space

---

### Post by Slim Odds on 2009-03-07
> **smooch101 said:**
> in a file browser right click a file then it tells you how much space

lol :p

---

