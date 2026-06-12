---
title: "azureus is broken"
date: 2006-03-08
forum: Desktop Environments
---

### Post by spartan777 on 2006-03-08
i installed azureus using automatix (awesome program). then i ran it, and it was fine for a while (see bottom). so it ran flawlessly, but then i updated to the 2.4 version. i restarted azureus, but it wouldn't start. i tried many things, uninstalling and reinstalling, but azureus wouldn't work. it doesn't respond whatsoever, even though automatix successfully installed it. what could the problem be with azureus? or is it a problem with java?



i was getting greens smilies even while my windows machine running azureus was getting all yellows, despite the ubuntu and windows machines have the same ports forwarded, and sitting on the same switch. weird.

EDIT: there's actually no problem w/ bittornado, that works fine.

---

### Post by adam.stokes on 2006-03-08
yea same here and its such a pain to debug java programs when they break :( i used automatix as well to install these apps

---

### Post by equal on 2006-03-08
Azureus 2.4 seems REALLY buggy to me, I've had nothing but problems. It insists that I'm behind a firewall, even when I disconnected my router and connected directly to my broadband modem. I do tech support for my ISP, so I know this modem, and there's no firewall in it!

---

### Post by rm -rf *.* on 2006-03-08
2.4 seems to work fine for me :D . I think the version provided from automatrix might be the problem, I would just grab it from sourceforge. I upgraded not to long ago and its been running fine, just run the application out of my home folder.

---

### Post by arnieboy on 2006-03-08
It has already been mentioned quite a few times that users should not attempt to upgrade to version 2.4 from the azureus updater. It will break azureus.
Automatix installs the debian package for azureus from the debian repositories. A native ubuntu deb package for azureus does not exist. when a package for 2.4 comes out, Automatix will be updated to install that version. In the meanwhile, my advice for all of u is to keep using version 2.3

---

### Post by spartan777 on 2006-03-12
the weird thing though is that it continues to not work, even after uninstalling (with apt-get) and reinstalling (with automatix). do i need to purge it using dpkg to get rid of something uninstalling doesn't?


ps: keep up the awesome work arnieboy. its people like you that make ubuntu so great, not to mention #1 on distro-watch.

---

### Post by taurus on 2006-03-12
Try removing both azureus and the config file in your home directory as well.  Then, install it again,
```

rm -rf ~/.Azureus

```

---

### Post by paul cooke on 2006-03-12
[QUOTE=arnieboy]It has already been mentioned quite a few times that users should not attempt to upgrade to version 2.4 from the azureus updater. It will break azureus.
Automatix installs the debian package for azureus from the debian repositories. A native ubuntu deb package for azureus does not exist. when a package for 2.4 comes out, Automatix will be updated to install that version. In the meanwhile, my advice for all of u is to keep using version 2.3[/QUOTE]

it might be noted that if you use the version of Azureus from their website, and install it for a local user, then that version works perfectly and upgrades itself perfectly. I stopped using the version available via apt-get a long time ago after it got upset that it couldn't automatically update itself unless I was root.

---

### Post by paul cooke on 2006-03-12
[QUOTE=spartan777]the weird thing though is that it continues to not work, even after uninstalling (with apt-get) and reinstalling (with automatix). do i need to purge it using dpkg to get rid of something uninstalling doesn't?
[/QUOTE]

you have to completely remove it. An ordinary uninstall leaves config files present. I use synaptic... easier to work with. I leave command line for when I really need command line, then the commands I use often are only a few "ups" in the history :)

---

### Post by spartan777 on 2006-03-12
thanks for the help, but i have finally found the answer i needed in another thread. artificial intelligence's post got everything working, using 2.4.0.0! here it is, with all the credit to artificial intelligence (and a complete uninstall in synaptic does seem necessary thank you taurus and paul cooke):

----------------------------------------------
Try this way:
Uninstall Azureus.

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.

Code:

cd /to/the/folder/where/you/saved/azureus sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/ sudo chown -R root:root /opt/azureus/ smeg


Pick Internet and click New Entry

Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png

press ok.
-----------------------------------------------

the only question i have now is, how does this all work since, as arnieboy said, there is no native .deb package? is it just because it's a java app, or what? i guess i should read up on packages.

---

### Post by s|k on 2006-03-12
2.4 works fine for me, I think it must be the way in which you updated it. Yes actually that's how I did it (your last post).

---

