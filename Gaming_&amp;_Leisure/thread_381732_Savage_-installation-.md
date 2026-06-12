---
title: "Savage -installation-"
date: 2007-03-11
forum: Gaming &amp; Leisure
---

### Post by kylet450 on 2007-03-11
Savage the battle of newerth is a RTS/FPS game developed by s2games that is available on both Linux and Windows. In this blog entry i will explain how to install the game using Ubuntu Linux (a Debian GNU/Linux deviant).
I assume because Savage is no longer in development the game is free to those who know. The CD-Key servers no longer authorize, meaning once you have the game you can play. So, go ahead and download the game. Via terminal

-------------------------------------------------------------

1). Type in termanial **"wget http://downloads.s2games.com/online_orders/savage_linux.sh.gz"**

2). Then cd over to were you downloaded it, then type: **"gzip -d savage_linux.sh.gz"**

3). Once done type: **"sh savage_linux.sh"**

 Once completed DO NOT PLAY! The game will need to be updated, so go ahead and exit.


4). Type this ( its an update ) **"wget http://www.nofrag.com/fichiers/savage/patches/499/savage_patch_200b.tar.gz"**

5). And this: **"wget http://www.nofrag.com/fichiers/savage/patches/537/savage_patch_200b_to_200c.tar.gz"**

6). Next copy all your patches from your home directory (or were ever you downloaded) to ~/games/Savage. In terminal copy and extract (overwriting the existing files) like this for an example;

**" cp savage_patch* ~/games/Savage/"**
**"cd ~/games/Savage"**
**"tar xvzf savage_patch_200b.tar.gz"**
**"tar xvzf savage_patch_200b_to_200c.tar.gz"**

Those patchs will bring the game up to speed with the official releases. Unforutnally s2gamers quit on the savage development and never released a linux version of 2.00e. No problems, simply visit [http://subsentient.com/savage/](http://subsentient.com/savage/) and download (for linux) EX2. Again in terminal (still in ~/games/Savage);

**"wget http://subsentient.com/savage/EX2_5b.tar.gz"**
**"wget http://www.extremehitech.com/gobbler/EX2/EX2_5b.tar.gz"**

**"tar xvzf EX2_5b.tar.gz"**

Weee! Finally patched the whole way up to Savage v2.00e w/ functional in-game server browser and on line capability.

7). Next we fix the broken links to the void updater by editing the savage link right in your home directory.

**"cd ~"**
**"vi savage"**

[B]Alter ./savage.bin to read ./silverback.bin $@

For example; #!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd /home/czar/games/Savage
#LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./savage.bin /home/czar/games/Savage
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin $@ /home/czar/games/Savage
exit 0[/B]

~Fin of the installation. Now to play simply run ~/savage. A note of warning, if you are running default ubuntu or kubuntu you will need to install some graphics drivers. See [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) for a General - HOWTO: Latest NVIDIA drivers

----------------------------------------------------------------------- --------------------------------------------------------
:guitar: [http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux](http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux) :guitar:

---

### Post by StarscreamD on 2007-03-25
Uhm, most of these links are broken and the link you are referring to hasn't been updated for almost a year. And this isn't a blog entry: I hope you were the original author of that blog you copied/pasted.

:???:

I want an updated version of this FAQ but I'm afraid that you can't download 2.0b patch, I looked everywhere and I can't find it. Anyone else know where I could grab it? Or do I even need it? Thanks for the read.

---

### Post by Perfect Storm on 2007-03-25
It's a copy from a blog and I know that guy who wrote it and he wants credits/permission for such things, therefore thread closed. Also the howto was valid a year ago and not anymore. Thread closed as the howto is not function and/or can be misleading.

---

