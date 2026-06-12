---
title: "Ubuntu 12.04 LTS works well only on 'Recovery Mode'"
date: 2013-10-08
forum: Desktop Environments
---

### Post by iebng on 2013-10-08
Hi,

I am using Ubuntu 12.04, of recently my system shutdown due to CPU overheating, but after solving the hardware issue, i began to work on Ubuntu which was dual boot with Windows XP

The normal boot to Ubuntu could result in freeze, cursor or keyboard not responding.

I restarted and logged-in to_**Ubuntu recovery mode**_, and bypassed from there to resume normal boot, Here the Ubuntu works just fine.

Every time I need to go from Ubuntu Recovery Mode to resume normal boot to work on it.

My question is why Ubuntu freezes on normal boot, but not in Ubuntu Recovery Mode.

All the Ubuntu files are updated with latest releases.

I have 3 GHz Intel Quad Core processor, 4 GB of RAM, 256 MB Graphics Card. 500 GB HDD.

---

### Post by sudodus on 2013-10-08
It could be a problem with the graphics chip/card or the wifi chip/card (if you have one).

I think recovery mode uses the boot option ***nomodeset*** by default. If you add that boot option (or some other one) to the standard mode, it might also work. See these links

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

