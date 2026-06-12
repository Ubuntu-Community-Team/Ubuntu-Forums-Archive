---
title: "Installing Ubuntu with SteamOS"
date: 2014-06-29
forum: Debian
---

### Post by micah3 on 2014-06-29
My friend had installed SteamOS on my laptop on a new hardrive after my old one died, i'm not happy with SteamOS so i'm looking to switch to Ubuntu, though i'm not sure how at all. My main problem is finding and installing an ISO image burning program. If anyone could help out that would be great.

---

### Post by Frogs Hair on 2014-06-29
Hello !

See the popular pages link in my signature for other documentation. 

[http://www.ubuntu.com/download/](http://www.ubuntu.com/download/)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Edit: I am not familiar with what programs Steam OS includes , but many distributions include disk burner as a default program or in a software repository. In Ubuntu the default is Brasero. See the add and remove software application. [http://www.howtogeek.com/179883/how-to-use-the-steamos-desktop/](http://www.howtogeek.com/179883/how-to-use-the-steamos-desktop/)

---

### Post by Vladlenin5000 on 2014-06-29
> **micah3 said:**
> My main problem is finding and installing an ISO image burning program. 

SteamOS is a Debian based Linux distro like Ubuntu and it's geared to run Steam and its games. Even so it installs the full Debian desktop environment so chances are that you already have what you're looking for. However, I can't guarantee that because I never used it.

Keep in mind you can also create the installation media - DVD or USB -  in any other computer and then use it to reinstall the one with SteamOS.

---

### Post by micah3 on 2014-06-29
I can't find any software to burn ISO images, I downloaded one called Brasero but it won't open. Any ideas?

---

### Post by Vladlenin5000 on 2014-06-29
Brasero should work.

Have you tried to right-click the ISO file? With Brasero installed it should at least appear in the "open with..." list...

---

### Post by micah3 on 2014-06-29
I'll try that

---

### Post by micah3 on 2014-06-29
I right clicked the .iso file I downloaded from the Ubuntu website 

ubuntu-14.04-desktop-amd64.iso

I clicked "Open with Brasero disc burner" it then showed the Brasero logo and a loading circle at the top and after that nothing happens.

---

### Post by ptn107 on 2014-06-29
xfburn is popular and very simple. [click to install]("apt://xfburn")

---

### Post by micah3 on 2014-06-29
Clicked and did nothing.

---

### Post by Vladlenin5000 on 2014-06-29
Weird... but possible... but weird... 
What other options do you have there? What is the default program associated with ISO files (if any)?


Note: Although SteamOS is Linux and also Debian based it necessarily have a lot in common with Ubuntu but SteamOS ISN'T Ubuntu. It goes without saying we AREN'T the best people to help you with that and, as a matter of fact we don't support SteamOS here. I'm surprised your thread is still here. It should have been moved to "Other OS/Distro support" already...

Now, don't you have another computer with a full desktop OS (yes, even Windows will do) you can use to burn the media? SteamOS isn't intended for anything else than running Steam games - it has been designed for the Steam console - and I suspect they trimmed it down to the essential parts therefore many things we take for granted in a "normal" desktop OS may simply NOT be possible to use...

---

### Post by Vladlenin5000 on 2014-06-29
[http://steamcommunity.com/groups/steamuniverse/discussions/1/](http://steamcommunity.com/groups/steamuniverse/discussions/1/)

---

### Post by micah3 on 2014-06-30
No luck yet.

---

### Post by micah3 on 2014-07-01
anyone?

---

### Post by newb85 on 2014-07-01
Perhaps SteamOS doesn't ship with the necessary libraries for burning DVDs.  Please open a terminal and enter the following
```
apt-cache policy libdvdread4
```
and post the output.  Also,
```
apt-cache policy libdvdcss
```
and post the output.

---

### Post by micah3 on 2014-07-01
```
desktop@steamos:~$ apt-cache policy libdvdread4
N: Unable to locate package libdvdread4

```

```
desktop@steamos:~$ apt-cache policy libdvdcss
N: Unable to locate package libdvdcss


```

---

### Post by micah3 on 2014-07-03
bump

---

### Post by sisco311 on 2014-07-03
Moved to **Other OS/Distro Support**.

---

### Post by newb85 on 2014-07-03
Hmm...I don't think Brasero will burn a DVD without DVD libraries...
How about:
```
apt-cache search libdvd
```

---

