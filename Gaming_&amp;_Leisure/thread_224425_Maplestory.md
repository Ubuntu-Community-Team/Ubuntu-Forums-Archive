---
title: "Maplestory"
date: 2006-07-27
forum: Gaming &amp; Leisure
---

### Post by Dylan103 on 2006-07-27
Well, I've been back and forth between Ubuntu and Windows, Im wanting to go back, but one game is sorta keeping me. Maplestory.
If somebody can get it to work and post a little tut her for me to follow, remember im not really experienced in linux terminal yet, so just post the commands you use.
But if possible please help :p
Thanks in advanced, dylan.

---

### Post by navilon on 2006-07-28
It's a great game, I agree. But you really have only 2 choices if you want to be able to play under ubuntu.

[LIST=1]
[*]Emulation: This is your best choice because it will let you run the windows operating system on top of linux. Try [VMWare]("http://www.vmware.com")or [QEMU]("http://fabrice.bellard.free.fr/qemu/")
[*]Wine: This is usually a trial and error process and not very stable. [http://www.winehq.org]("http://www.winehq.org")
[/LIST]

Sadly, according to the wine application database, MapleStory is not yet compatible
[http://appdb.winehq.org/appview.php?iAppId=2341]("http://appdb.winehq.org/appview.php?iAppId=2341")

---

### Post by Dylan103 on 2006-07-28
How would I install using VMWare or QEMU, and wich would work best with least hassle?

---

### Post by navilon on 2006-07-28
QEMU is open source and there is a tutorial for getting it up and running here: [http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html](http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html)

VMWare has a free version of their software but catch is that you have to already have a pre built image of windows (think of this as an entire operating system grouped into one file). They provide you with images of operating systems like Ubuntu and Fedora Linux but you wont be able to find a pre built because of Microsoft's license agreement. (Windows isn't free and can not be legally distributed for free like Ubuntu can)

---

### Post by FizDev on 2006-07-28
Actually, I don't think VMWare and/or QEmu support games, try Cedega instead
[http://www.transgaming.com/]("http://www.transgaming.com/")

You can download and install the trial there. Cedega is an emulation software made specifically for running games. I'm not sure if it can run Maplestory but it's always worth the try. ;)

---

### Post by navilon on 2006-07-28
MapleStory is a 2D sidescroller, i bet it wont have a problem runnign under qemu.

---

### Post by Qwerty_ on 2006-07-28
> **navilon said:**
> MapleStory is a 2D sidescroller, i bet it wont have a problem runnign under qemu.

Yeah i saw it at a friends house and from the looks of it it should easily run under wine. As in no 3d graphics, the graphics are pretty basic however there might some problems talking to the net with it, However i am unsure.

---

### Post by navilon on 2006-07-28
Well, according the Wine, the only test done on maplestory was faulty.

---

### Post by LordRaiden on 2006-07-28
It can talk to the net fine. It's the fact that MapleStory has Gameguard. Gameguard "protects" MapleStory from hacking. It uses hardware information that it gets from Windows. Wine does not currently support GameGuard, and apparently it never will. GameGuard has been considered a vulnerability on Windows by several security analysts (Search for it on the Internet). The people who make GameGuard "say" that they are working on a Linux version, but apparently they recommend you to install Windows.

It's sort of annoying, I know, but it is the truth.

---

### Post by Dylan103 on 2006-07-28
Ok, so, would it work or not? Ive gotten yes's and knows, but, could somebody try it out please?

---

### Post by navilon on 2006-07-28
It will work in QEMU and VMWare.
It will not work in WINE.

---

### Post by asantainnasa on 2007-02-15
> **navilon said:**
> It will work in QEMU and VMWare.
It will not work in WINE.

yes, it is true that it won't work under wine or cedega, since it has gameguard problems
but it won't work in VMWare either, 
VMWare doesn't have a signed graphics driver, thus directX/maplestory does not recognize the graphics driver, and won't execute anything that requires directX
but parallels station, some program similar to VMWare, (parallels.com) has announced that in the next version, it will release the support for maplestory that was specially requested.
So hope they'll do it fast =]
but now i'm just switching b/t linux and windows
my windows is a gaming station, which really isn't bad, since you get higher fps for fps games and much better graphics rendering for RTS.

---

