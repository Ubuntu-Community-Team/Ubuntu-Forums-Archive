---
title: "Can't fully un-install extra DE's"
date: 2014-06-28
forum: Desktop Environments
---

### Post by kmdude344 on 2014-06-28
A few months ago I downloaded a few extra DE's to test such as KDE and XFCE (with the sudo apt-get install kubuntu-desktop and xubuntu-desktop). When I removed them them with sudo apt-get remove whatever-desktop, It did remove KDE and most of its dependencies and programs, but the kubuntu splashscreen which had replaced the ubuntu one stayed and XFCE didn't get removed at all. Does anyone know what I'm doing wrong? And ever since I've downloaded the Xubuntu desktop specifically, I cannot download updates from the update centre. I'm using Ubuntu 14.04

---

### Post by grahammechanical on 2014-06-28
I had a similar experience the other year when I tried out alternative desktops. I ended up re-installing. Now, if I want to see how the other flavours are doing I install the flavour in another partition. I have a few 10 GB to 20 GB partitions just for messing around like this.

As far as I can tell the problem is caused when the installation of the alternative desktop overwrites certain configuration files relating to splash screens and the sort. These configurations files do not get replace when the alternative desktop is un-installed. There is no mechanism for doing that.

Regards.

---

### Post by AnotherKevin on 2014-06-29
> **kmdude344 said:**
> A few months ago I downloaded a few extra DE's to test such as KDE and XFCE (with the sudo apt-get install kubuntu-desktop and xubuntu-desktop). When I removed them them with sudo apt-get remove whatever-desktop, It did remove KDE and most of its dependencies and programs, but the kubuntu splashscreen which had replaced the ubuntu one stayed and XFCE didn't get removed at all. Does anyone know what I'm doing wrong? And ever since I've downloaded the Xubuntu desktop specifically, I cannot download updates from the update centre. I'm using Ubuntu 14.04


I had a similar issue:  I installed XFCE and KDE.  When using apt-get to do the install/uninstall, things were left behind that would show up under other DEs.  I installed Synaptic and did a search within Synaptic for Xubuntu and XFCE and removed the majority of packages that came up with that search (KDE is the DE I decided to stick with).  

Synaptic makes it _very easy_ to remove anything, or to install anything.  IMHO     :KS

Kevin

---

### Post by Bucky Ball on 2014-06-29
After the horse has bolted ... but better to install just the desktop environment, NOT the whole desktop of the flavour. For xfce, for instance, install xfce4, NOT xubuntu-desktop. That is like having Ubuntu and Xubuntu crammed onto one partition.

I think you might want:

```
sudo apt-get purge kubuntu-desktop
```

... and the same replacing 'kubuntu' with 'xubuntu' and then:

```
sudo apt-get  autoremove
```

May improve things, but don't think you'll ever get rid of everything.

---

### Post by kmdude344 on 2014-07-05
> **grahammechanical said:**
> I had a similar experience the other year when I tried out alternative desktops. I ended up re-installing. Now, if I want to see how the other flavours are doing I install the flavour in another partition. I have a few 10 GB to 20 GB partitions just for messing around like this.

As far as I can tell the problem is caused when the installation of the alternative desktop overwrites certain configuration files relating to splash screens and the sort. These configurations files do not get replace when the alternative desktop is un-installed. There is no mechanism for doing that.

Regards.

I could do that but I'd rather not as I have nearly 150 gb of files I'd like to keep (games and data for the most part) and is very in likely I'll find a thumb drive that can hold that much.

---

### Post by kmdude344 on 2014-07-05
> **Bucky Ball said:**
> After the horse has bolted ... but better to install just the desktop environment, NOT the whole desktop of the flavour. For xfce, for instance, install xfce4, NOT xubuntu-desktop. That is like having Ubuntu and Xubuntu crammed onto one partition.

I think you might want:

```
sudo apt-get purge kubuntu-desktop
```

... and the same replacing 'kubuntu' with 'xubuntu' and then:

```
sudo apt-get  autoremove
```

May improve things, but don't think you'll ever get rid of everything.

I don't think that'll work as I've already tried the simple apt-get remove and the system would reconize It as being all gone even if I used those commands.

---

### Post by Dennis N on 2014-07-05
For what its worth, as an example of the problems of reversing the installation of a desktop package, installation of **xubuntu-desktop** on my Lubuntu 14.04 system would result in the installation of 307 new packages.

Then, trying to remove them later with **apt-get remove xubuntu-desktop** would remove only 1 of those 307 packages - xubuntu-desktop. The other 306 are still installed. 

(This is because xubuntu-desktop is an example of a metapackage, the installation of which causes other packages to be installed. That is it's purpose. But it doesn't work in reverse.)

Installing the desktop environment xfce instead (as mentioned in post #4) would result in the installation of only 33 new packages. It is also a metapackage.

---

### Post by Bucky Ball on 2014-07-06
Once you're there, pretty hard to go back ...

---

### Post by vanadium on 2014-07-06
Installing a metapackage indeed pulls in all dependencies. Removing the metapackage just removes the metapackage: you need to remove the other packages (applications, desktop environment) yourself. [Psychocats](http://www.psychocats.net/ubuntucat/?s=Pure+Ubuntu) used to post command one liners to do this, but it has not been done for 13.10 and above. Do not try a line for a version different than that of your own. It might break your installation.

To revert to the default Ubuntu login manager, you may find some inspiration here: [http://askubuntu.com/questions/371742/how-to-restore-ubuntu-login-screen-after-lubuntu-install](http://askubuntu.com/questions/371742/how-to-restore-ubuntu-login-screen-after-lubuntu-install)

There can be a good reason to mix desktop environments, notably if different users want different DE's (and you as a sysadmin want to to provide them that freedom). It has its side effect, and fully reverting the installation of another flavour of Ubuntu within your current DE involves manual work.

---

### Post by PJs Ronin on 2014-07-06
There is an old blog post from PsychoCat [here]("http://www.psychocats.net/ubuntu/pureubuntu") that may help.

---

### Post by Bucky Ball on 2014-07-06
> **PJs Ronin said:**
> There is an old blog post from PsychoCat [here]("http://www.psychocats.net/ubuntu/pureubuntu") that may help.

This:

> **vanadium said:**
> [Psychocats](http://www.psychocats.net/ubuntucat/?s=Pure+Ubuntu) used to post command one liners to do this, but it has not been done for 13.10 and above. _Do not try a line for a version different than that of your own. It might break your installation._



---

### Post by kmdude344 on 2014-07-10
Well I've bought an external hard drive and im now going to just reinstall ubuntu. At the moment that seems like the only option.

---

### Post by grumblebum2 on 2014-07-10
Would it not be possible to find the extra packages installed by using a live cd/usb.
Say you installed xubuntu-desktop but now wanted to completely uninstall.

Boot up a live cd/usb of your installed release and simulate an xubuntu-desktop install.
```
sudo apt-get --simulate install xubuntu-desktop
```
Copy from the terminal the list of new packages to be installed to somewhere you can access them.

Then boot into your installed desktop and run
```
sudo apt-get remove [COLOR="#808080"]<list of packages>[/COLOR]
```

---

