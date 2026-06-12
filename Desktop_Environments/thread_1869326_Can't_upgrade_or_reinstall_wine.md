---
title: "Can't upgrade or reinstall wine"
date: 2011-10-25
forum: Desktop Environments
---

### Post by Acharn on 2011-10-25
I'm still running 11.04 Natty Narwhal, because I've seen a lot of little glitches with 11.10, but since 11.10 became available I've had an upgrading problem. I had wine 1.2.2 installed, using the meta package in the Software Center. The first day I noticed an upgrade to 11.10 was available, I installed a bunch of security upgrades. There were some upgrades to wine at the bottom of the list, but if I left them selected I couldn't run any of the upgrades. I kept getting the message, "Requires installation of untrusted packages." The details indicated the problem was with "ttf-symbol-replacement-wine1.3 wine wine1.3 win-1.3-gecko winetricks," which I gather is a list of packages required but not allowed. About the same time two windows programs, Ares Galaxy and Bit Che, started working; they hadn't been accessing the Internet before. However at least one windows game, Codename Panzers: Phase One, stopped working.

Today I decided to try a new installation of wine, to see if that would upgrade to the new stable version of 1.2.3 (which I really want). I was able to uninstall wine, but now I get the same message when I try to install the meta package through the Software Center. So I want to update wine to version 1.2.3, I don't really want the latest, greatest, cutting-edge version of 1.3.30 or whatever it is, but I can't install any version through the Software Center. Can anybody suggest a way forward?

---

### Post by Acharn on 2011-10-25
Someone over at the WineHq Forum gave me the answer. It seems there is a Ubuntu Wine Team that has its own repository. There is a web page that explains clearly how to add their repository [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)  I don't understand why I was able to install 1.2.2 without using that repository, but not 1.2.3, nor why I couldn't find any mention of them or their repository in the Ubuntu forums, nor why the Ubuntu Software Center couldn't have given a more descriptive error message.

---

