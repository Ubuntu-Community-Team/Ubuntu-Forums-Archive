---
title: "anyone installed latest kerry beagle on edgy ?"
date: 2007-02-07
forum: Desktop Environments
---

### Post by brazzmonkey on 2007-02-07
i have installed latest kerry beagle on other distros, and i must say version 0.2.1 features quite a lot of improvements when compared to the one that comes with edgy (0.1).

too bad, i don't seem to be able to install it on kubuntu edgy, sources compile and install fine (with no apparent errors), but kerry is nowhere to be found. is there anything special to do to make it work ?

---

### Post by scido06 on 2007-03-09
Hi,
I installed last kerry package (0.2.1) from feisty using prevu (see [http://www.ubuntuforums.org/showthread.php?t=268687)](http://www.ubuntuforums.org/showthread.php?t=268687)).

1. install prevu. See the guide till point 3 (initialize prevu)
2. create new packages of beagle (for kerry 0.2.1 you need libbeagle-dev) using this command:

```
prevu beagle
```

3. Install new updated packages from local prevu repository (in my case beagle and libbeagle0). It'll download several new packages from edgy repository: it's all OK

4. update prevu chroot and THEN create new packages of kerry with prevu

```
sudo prevu-update
prevu kerry
```

5. install new packages and enjoy it

If you trust me, I can move my packages in some part of the net and put a link here.

Bye
Scido

---

### Post by brazzmonkey on 2007-03-09
> **scido06 said:**
> If you trust me, I can move my packages in some part of the net and put a link here.

should i ?
actually installed prevu (btw, did you know it means something like "expected" in french ?), but i freaked out when i ran adept after i changed my sources.list : it asked me to upgrade to feisty !

---

### Post by brazzmonkey on 2007-03-09
i gave up because it was about to download and compile more than 100 packages ! and now adept keeps nagging me about upgrading to feisty !
this prevu thing looks somewhat dangerous...

---

### Post by scido06 on 2007-03-12
I uploaded compiled files in [rapidshare ]("http://rapidshare.com/files/20711420/kerry_beagle.zip.html") This archive has these files (compiled using prevu):

```

beagle_0.2.16-0ubuntu4~6.10prevu1_i386.deb
beagle-backend-evolution_0.2.16-0ubuntu4~6.10prevu1_all.deb
beagle-dev_0.2.16-0ubuntu4~6.10prevu1_i386.deb
kerry_0.2.1-0ubuntu2~6.10prevu1_i386.deb
libbeagle0_0.2.16-0ubuntu4~6.10prevu1_i386.deb
libbeagle-dev_0.2.16-0ubuntu4~6.10prevu1_i386.deb
mozilla-beagle_0.2.16-0ubuntu4~6.10prevu1_all.deb
python-beagle_0.2.16-0ubuntu4~6.10prevu1_i386.deb

```

To install kerry, first you have to install new beagle packages, beagle and libbeagle:

```

sudo dpkg -i beagle_0.2.16-0ubuntu4~6.10prevu1_i386.deb libbeagle0_0.2.16-0ubuntu4~6.10prevu1_i386.deb 

```

This command will fail because you need to update some packages, already in edgy repository. Then, type apt-get -f install to resolve any problems:

```

sudo apt-get -f install

```

If everything goes right, install kerry

```

sudo dpkg -i kerry_0.2.1-0ubuntu2~6.10prevu1_i386.deb

```

If everything is ok, now you will have new kerry version on you pc.

I found a problem with beagle startup. new version of beagle copies startup scripts in a different directory, so when you start a kde session, beagle doesn't start automatically.
I resolved this creating symlink from new directory to old directory, used by kde to autostart application. to do that, use this code:

```

sudo ln -s /etc/xdg/autostart/beagled-autostart /usr/share/autostart/beagled-autostart
sudo ln -s /etc/xdg/autostart/beagled /usr/share/autostart/beagled

```

I hope everything will work. If you need some help, write here and I'll try to help you

bye
Scido

---

