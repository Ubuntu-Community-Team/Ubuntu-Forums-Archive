---
title: "Stellarium in Repo?"
date: 2019-01-26
forum: Gaming &amp; Leisure
---

### Post by Daveski17 on 2019-01-26
I'm just curious, but why has Stellarium disappeared from Ubuntu Software?

[ATTACH=CONFIG]282311[/ATTACH]

Furthermore, it seems to have disappeared from Installed Software on my laptop. Although it's still actually there. 

[ATTACH=CONFIG]282312[/ATTACH]

Can anyone shed any light on this please?

Thanks.

---

### Post by #&amp;thj^% on 2019-01-26
I don't know why but if you want/need it:
```
sudo add-apt-repository ppa:stellarium/stellarium-releases
sudo apt update
```
This has always been very well maintained with "my" experience using it (FWIW). [https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases](https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases)

---

### Post by monkeybrain20122 on 2019-01-26
well it is. Which Ubuntu is it? (Screenshot from 18.04)

If you are using Ubuntu 16.04 then maybe it doesn't show up in the Software Centre since the SC's listing is not complete and they are adding more stuffs as time goes on. But you can find it in synaptic.

Anyway the repo's version is old. To get the newest version you can either use this [ppa]("https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases")
or download the appimage from stellarium's [website]("https://stellarium.org/")
To use the appimage, right click, in Properties > Permission check allow to run as a program then you can just run it by clicking.
Then there is a flatpak which will also be updated regularly as you see from my screenshot but that is because I have installed flatpak and added the flathub repo, it won't show in your system if you haven't done that.

---

### Post by Daveski17 on 2019-01-26
> **1fallen said:**
> I don't know why but if you want/need it:
```
sudo add-apt-repository ppa:stellarium/stellarium-releases
sudo apt update
```
This has always been very well maintained with "my" experience using it (FWIW). [https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases](https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases)

OK thanks.

---

### Post by Daveski17 on 2019-01-26
> **monkeybrain20122 said:**
> well it is. Which Ubuntu is it? (Screenshot from 18.04)

If you are using Ubuntu 16.04 then maybe it doesn't show up in the Software Centre since the SC's listing is not complete and they are adding more stuffs as time goes on. But you can find it in synaptic.

Anyway the repo's version is old. To get the newest version you can either use this [ppa]("https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases")
or download the appimage from stellarium's [website]("https://stellarium.org/")
To use the appimage, right click, in Properties > Permission check allow to run as a program then you can just run it by clicking.

Thanks. I'm running 16.04 LTS, before that I ran 14.04 for years and Stellarium has always been in the repo. It was in a few weeks ago as I uninstalled then reinstalled it from the repo. I have a copy of it on my laptop. I don't understand why Stellarium has disappeared from the installed programs list though, as I can still use it.

---

### Post by Daveski17 on 2019-01-27
It's back!

[ATTACH=CONFIG]282324[/ATTACH]

:D

---

### Post by Frogs Hair on 2019-01-27
I see Stellarium in synaptic tough you'll probably get the latest updates with the PPA. Enjoy !

---

### Post by Daveski17 on 2019-01-27
> **Frogs Hair said:**
> I see Stellarium in synaptic tough you'll probably get the latest updates with the PPA. Enjoy !

Thanks. I'm guessing that its temporary disappearance was due to site maintenance on the repo.

---

### Post by oldrocker99 on 2019-02-04
My go-to program has been Aqualung, a gapless music player, which disappeared from the repos some time ago. There was a PPA, which has not been updated since Trusty Tahr, and 18.04 is Cosmic Cuttlefish, so it's been quite some time.

So, having a few successes with compiling source code, I downloaded the Aqualung source code, read what dependencies are required, including compiling GTK2, and, finally the missing -dev files, and successfully compiled the program. 

It's really not as hard as people think, and the compiled program will be customized for your system. Obviously, 98% of my programs are from the repos, and some PPAs.

---

