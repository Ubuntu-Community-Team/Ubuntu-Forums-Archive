---
title: "wireless tried everything"
date: 2009-02-05
forum: General Help
---

### Post by jorge999 on 2009-02-05
I have been trying to fix this for weeks, I am a complete ubuntu noob, I thought it was meant to be easier to use and faster than windows vista. However, I am having problems with my atheros AR5007 WIRELESS CARD for my COMPAQ PRESARIO. I have ubuntu 8.04 hardy heron installed. I know that this problem has been answered to in many threads but all the ones i have tried are out of date or have been removed and therefore have been unsuccesful. Atm im connected to internet with a wired connection. I might give up soon and go back to vista, but id like to stay with linux if i can get some help to get it fixed. Thanks

---

### Post by whitegourd on 2009-02-05
Would you be able to provide more detail of what your wireless issue is?  What have you already tried already?

---

### Post by jorge999 on 2009-02-05
The problem is that it is not detected at all. On the network options i only can choose a wired connection. Im not sure of all the ones i tried but the last one was instructions from the ubuntu site, which had instructions on how to install the atheros driver on the acer aspire one for ubuntu 8.04 hardy. It didnt work... btw im very impressed by how fast people respond to these threads, seems like this site works really well thanks

---

### Post by redilyn on 2009-02-05
*nm*

---

### Post by redilyn on 2009-02-05
Perhaps try the madwifi driver, worked much better for my eeepc

If you have Atheros AR5007 wireless network adapter follow this procedure to make it work in ubuntu 8.04

For i386 Users

First go to System&#8211;>Administration&#8211;>Hardware Drivers&#8221; and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then Reboot your system.

Then open the terminal from Applications&#8211;>Accessories&#8211;>Terminal and copy the following command

```

sudo apt-get install build-essential

```

```

http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz

```

```

tar xfz madwifi-0.9.4.tar.gz

```

```

cd madwifi-0.9.4

```

```

make

```

```

sudo make install

```

```

sudo modprobe ath_pci

```

```

sudo reboot

```
That&#8217;s it now your wireless should work without any problem.

---

### Post by whitegourd on 2009-02-05
Have you tried this link already?  Unfortunately I don't have the same setup hardware that you do.

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by wolfen69 on 2009-02-05
[This]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html") will get you up and running.

---

### Post by jorge999 on 2009-02-05
Ive already tried this one and it doesnt work. I think it is because the link is out of date- wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

---

### Post by jorge999 on 2009-02-05
it says this

---

### Post by 5BallJuggler on 2009-02-05
This may help

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by whitegourd on 2009-02-05
> **jorge999 said:**
> Ive already tried this one and it doesnt work. I think it is because the link is out of date- wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

# Maybe try the one on the repos ...
sudo apt-get install madwifi-tools

---

### Post by jorge999 on 2009-02-05
My wirless is an atheros ar5007 not AR242x 802.11
I tried what redilyn said but this happened....

---

### Post by 5BallJuggler on 2009-02-05
> **jorge999 said:**
> My wirless is an atheros ar5007 not AR242x 802.11
I tried what redilyn said but this happened....

I know it is a different card, but enabling the backports may be of some use.
it's up to you.

---

### Post by redilyn on 2009-02-05
Please go back and try to follow my directions again.

I've updated the link so you should be able to do it now.

---

### Post by jorge999 on 2009-02-05
just done ridelyns method, didnt work as i still cannot detect wireless drivers. Am i meant to activate the HAL again?

---

### Post by redilyn on 2009-02-05
You can give it a try and see if it helps.

Also, right click on the network icon and choose connection information.

What driver is listed?

---

### Post by jorge999 on 2009-02-05
it says the wireless hardware is in use, ive attached a screenshot of that plus my connection information for the wired conndction. im about to reboot again, maybe it will work with sum luck, i hope...

---

### Post by jorge999 on 2009-02-05
still doesnt work, im gonna try enabling the backports, im not sure if ive already done this, maybe it was included in the code from redilyn

---

### Post by jorge999 on 2009-02-05
rebooted, and now it doesnt even say ´in use´ on the hardware screen!

---

### Post by whitegourd on 2009-02-05
Looks like someone else is having a similar issue w/ your type of card as well ...

[http://ubuntuforums.org/showthread.php?p=6682205#post6682205](http://ubuntuforums.org/showthread.php?p=6682205#post6682205)

---

### Post by jorge999 on 2009-02-05
thanks for all the help but it doesnt seem to work. At least it now says in use when i use redilyns code. However ive wasted too much time on this so im goin to give up. Ill go back to windows as at least my wifi works with that. Hopefully windows 7 will be better than vista.

---

### Post by Bigneil on 2009-02-05
Don't loose hope just yet.  

I felt like giving up when i tried to get my wireless card working on my old sony laptop.

it was one of those cards that plugs into the pcmcia slot. it would never work so my only internet was also on a pcmcia slot ethernet adapter. the two card could never be in at the same time. in the end, the solution was simple.  I borrowed one of those USB wireless dongle things and i found that while i was connected to the internet with it, the wireless pcmcia card was still in its slot. Ubuntu then detected it and informed me that there were propriety drivers available and did i want to install them?

i did, and it worked. 

LOL, it had me stumped for over a year.

I am not saying that your solution will be the same as mine,but it could just be something as simple that has been overlooked.

---

### Post by jorge999 on 2009-02-05
Ive used a wireless dongle and that works fine, it´s just such an inconveniance to have a big usb stick sticking out of your laptop. I jst hoped i could get it working as it is meant to. Mind you it wasnt all in vain, i discovered a lot about linux and different os that i didnt know b4.

---

### Post by redilyn on 2009-02-05
Before giving up please upgrade to 8.10

As i said earlier it seems to be better for wireless in my experience

---

### Post by jorge999 on 2009-02-06
Is 8.1 intrepid the best then?

---

### Post by 3rdalbum on 2009-02-06
jorge999: Upgrade to Intrepid. There is an excellent Atheros driver available in the Intrepid Backports repository, that should work with your card.

Upgrade, then enable the Backports repository in System > Administration > Software Sources. Then there's a package available called "linux-backports-modules-intrepid-generic". Install that. Add "ath_pci" to the /etc/modprobe.d/blacklist file, and add "ath5k" to the /etc/modules file. Reboot, and the better driver will be in action.

Why wouldn't the latest stable version of Ubuntu be better than the one before?

---

