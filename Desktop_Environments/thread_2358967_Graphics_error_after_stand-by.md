---
title: "Graphics error after stand-by"
date: 2017-04-19
forum: Desktop Environments
---

### Post by lschw on 2017-04-19
Hi everybody,

My Ubuntu 16.04 behaves strangely after reactivating from stand-by mode. There is a strange graphic error (see picture).
Has anybody already faced this problem and knows a solution?

Best,
lschw

---

### Post by scriber on 2017-04-19
Is your graphic card Nvidia ?

---

### Post by k999 on 2017-04-20
I'm seeing very similar artifacts. The artifacts around this terminal window are very close to what you have, and then I also have those artifacts around the menu that is showing. It's interesting that these artifacts appear on screenshots.

[ATTACH=CONFIG]274679[/ATTACH]

I'm on an Asus U36S laptop, which has dual graphics adapters. I think the idea is one for low power use and one for performance. (This makes color calibration next to impossible, not recommended.)

$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce GT 520M] (rev a1)

$ lspci | grep -i graphics
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

The driver is the nvidia-375 package, "NVIDIA binary driver - version 375.39".

Any ideas what I can do to debug this? As with OP, this only happens after standby. And it only started fairly recently, past few weeks or so.

Edit: I'm also on Ubuntu 16.04.

---

### Post by scriber on 2017-04-20
Surprised you haven't got the new Nvidia driver that fixed all that.

V381.09  I believe it was, totally fixed all my issues.

It should show up in the drivers section of the Software manager.

---

### Post by k999 on 2017-04-20
scriber, is that on Ubuntu 16.04? Perhaps you're on Ubuntu 16.10? nvidia-375 is the latest driver I see. Perhaps I'd need to download something manually, or add a ppa to get a newer version, but if so this is still an Ubuntu issue that ought to be fixed. I'll wait a bit more to see if there is a "correct" fix before looking for drivers from other sources.

---

### Post by scriber on 2017-04-20
Yes, it's for 16.04 which is what I'm on.

It's definitely in the driver update section, at least it was for me and others.

Just checked here, it's in the Software & Updates  section ( not the Ubuntu Update folder ) under additional Drivers, it says, Nvidia Binary driver version 381.09 from Nvidia-381 (open source)

You should find it if you go to System Settings and the Software & Updates folder is there.

---

### Post by k999 on 2017-04-20
I don't see that package. Here's what my "Additional Drivers" looks like:

[ATTACH=CONFIG]274681[/ATTACH]

In addition, a search on packages.ubuntu.com does not show nvidia-381, [nvidia-375 is the latest version for xenial]("http://packages.ubuntu.com/search?suite=xenial&searchon=names&keywords=nvidia-"). [Even yakkety only has nvidia-375]("http://packages.ubuntu.com/search?suite=yakkety&searchon=names&keywords=nvidia-"). I think you've added the ppa at [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa), they have 381.09 as the current beta.

---

### Post by scriber on 2017-04-20
> **k999 said:**
> I don't see that package. Here's what my "Additional Drivers" looks like:

[ATTACH=CONFIG]274681[/ATTACH]

In addition, a search on packages.ubuntu.com does not show nvidia-381, [nvidia-375 is the latest version for xenial]("http://packages.ubuntu.com/search?suite=xenial&searchon=names&keywords=nvidia-"). [Even yakkety only has nvidia-375]("http://packages.ubuntu.com/search?suite=yakkety&searchon=names&keywords=nvidia-"). I think you've added the ppa at [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa), they have 381.09 as the current beta.

Different than mine.

They HAD 381.09 as beta for a while, then they released the new version I have.

I don't know what else to say :confused:

---

### Post by mc4man on 2017-04-20
> **scriber said:**
> Different than mine.

They HAD 381.09 as beta for a while, then they released the new version I have.

I definitely didn't add the ppa.

I don't know what else to say :confused:
You don't have to say anything, post results of
```
apt-cache policy nvidia-381 
```

---

### Post by scriber on 2017-04-20
[ATTACH=CONFIG]274682[/ATTACH]

Took me awhile to figure out how to do an attachment !

```
nvidia-381:
  Installed: 381.09-0ubuntu0~gpu16.04.1
  Candidate: 381.09-0ubuntu0~gpu16.04.1
  Version table:
 *** 381.09-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

Sorry, I'm fairly new to Ubuntu, some things take me a while to figure out.

---

### Post by mc4man on 2017-04-20
> **scriber said:**
> 

Took me awhile to figure out how to do an attachment !

```
nvidia-381:
  Installed: 381.09-0ubuntu0~gpu16.04.1
  Candidate: 381.09-0ubuntu0~gpu16.04.1
  Version table:
 *** 381.09-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

Sorry, I'm fairly new to Ubuntu, some things take me a while to figure out.
so that is from the graphics-drivers ppa, you must have added it at some point..

---

