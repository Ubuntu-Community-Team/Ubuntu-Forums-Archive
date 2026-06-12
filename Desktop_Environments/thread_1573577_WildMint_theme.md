---
title: "WildMint theme"
date: 2010-09-12
forum: Desktop Environments
---

### Post by DarthScape on 2010-09-12
On Linux Mint, there is this theme called WildMint, looks somewhat like an older Ubuntu Studio theme. Anyway, I have been trying to find how to get it to work on Ubuntu instead of Mint. It is nowhere to be found on Gnome-Look and I've tried to search everywhere for it. Also, I've tried just copying the folder from /usr/share/themes but I just get errors even when running Nautilus under gksudo.

Any ideas would be great! Thanks in advance.

---

### Post by ankspo71 on 2010-09-13
Hi,
You can find WildMint in LinuxMint's repository:
[http://packages.linuxmint.com/list.php?release=Isadora](http://packages.linuxmint.com/list.php?release=Isadora)
WildMint is inside the package "mint-artwork-gnome"
(older packages can be found here [http://packages.linuxmint.com/](http://packages.linuxmint.com/) )

you can try to extract the WildMint theme from the mint-artwork-gnome deb package to see if it will work without installing any extra theme engines.

PS> You can create a hidden folder named ".themes" inside your home folder and place the WildMint theme folder in there.

---

### Post by DarthScape on 2010-09-13
Thanks! :D Worked perfect on Karmic, off to try lucid now. The only other thing I had to do was install the aurora gtk engine, but that was pretty easy.

---

