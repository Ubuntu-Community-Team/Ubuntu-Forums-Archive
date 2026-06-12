---
title: "System freezes with most tux games"
date: 2005-12-13
forum: Gaming &amp; Leisure
---

### Post by eaglescout1984 on 2005-12-13
Unlike games that you can get at a store for a Windows system, the games that you can add for Linux don't list system requirements, so I'm not sure if this could be the issue.
Anyway, I've noticed Tux Kart and Slune freeze when I enter the first level. Super Tux will freeze if I turn "Open GL" on. This is without other programs open. These are my specs (Don't laugh at my processor speed, I haven't gotten around to changing it with school.):

Processor: AMD Duron 1.1 GHz
Swap Space: 1 GB (7200 RPM)
Memory: 768 KB (PC133)
Video Card: ATi Radeon 128 MB

Would this be the reason the games freeze the system, or is it likely another cause?

---

### Post by teaker1s on 2005-12-13
standard nv driver doesn't support open gl you need a different driver, I'm guessing ati is the same

---

### Post by Biased turkey on 2005-12-13
It looks like you don't have 3D graphics hardware acceleration installed.
An analogy with Windows: If you just install Windows XP you won't be able to play 3D games. In order to do that you must install the driver that comes with the CDROM supplied when you purchase your video board. At the same time, the DirectX ( Microsoft 3D graphics libraries ) are installed 

With Ubuntu that's exactly the same, so you must enable 3D hardware acceleration by installing ATI driver.

There is some exception with ATI boards: for some  ( old )  ATI models, 3D hardware acceleration is installed by Ubuntu out of the box ( that's the case for the Radeon 8500 for example )
How do you know if 3D acceleration is enabled?
Run the following command:
glxinfo
It will display a message and the 2nd or 3rd line of it is:
Direct rendering: Yes.

If itsn't it will display:
Direct rendering: no

So first, post the result of what you get with the glxinfo ciommand.

To install 3D hardware acceleration, follow the procedure at:
[https://wiki.ubuntu.com/BinaryDriverHowto]("https://wiki.ubuntu.com/BinaryDriverHowto")

That should get you started.

---

### Post by eaglescout1984 on 2005-12-13
It gave me direct rendering: yes.

I went ahead and installed the hardware acceleration, and as far as I can tell it won't freeze the system, but it slowed the game down a lot.

---

### Post by eaglescout1984 on 2005-12-13
Okay, I got it working now. I forgot to change the driver from "ati" to "fgrlx" after installing it. So far, so good.

---

### Post by jimmy41 on 2005-12-14
Great instructions here for ATI drivers:  [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

My 9550 isn't recognized properly so it takes a few extra steps...but still very clear instructions.

Easy way to see if your drivers are installed right...

run:
```
$ fglrxinfo
```
if the results have anything mentioning MESA they weren't installed/configured right.

---

