---
title: "Dell dimension 4300"
date: 2008-03-26
forum: Dell  Ubuntu Support
---

### Post by pibb69173 on 2008-03-26
yea so i am running a dell dimension dektop, 512 ram, ATI rage 128 Pro Ultra TF video card running ubuntu 7.10 and i was wondering were i could get updated drivers for my video card cause i dont think im using the latest, and yes i know that my video card is discontinued, and also ubunu dosnt recognize my modem(stock)

---

### Post by unoodles on 2008-03-26
To get the latest updates for anything (including drivers) you can type:
sudo apt-get update
sudo apt-get upgrade

or you can use the update tool located at System->Administration->Update Manager.

you will need internet access to do this.

as for your modem i would reccommend reading:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by pibb69173 on 2008-03-26

ok thanx and the only problem is that i dont have internet on my comp i use my psp also theres something wrong with ur link also thanx again

---

### Post by unoodles on 2008-03-26
The link is working fine for me.

There is no easy way of updating a computer without internet.
the way you would have to do it is go to packages.ubuntu.com and download the new files one-by-one. You may just want to wait until hardy comes out, and you will get the latest driver packages.

---

### Post by pibb69173 on 2008-03-26
what i did was edit my html and got all the pckages then i ran into major trouble i installed a package called e2fsprogs 1.40 then it told me the package was broken and i cant install any more packages without removing it and if you didnt know its an essential part of ur system and if u remove it then it removes a tune of essential packages so now i cant finishing updating and cant install any .deb's or remove the broken package, im in a state of panic plz plz help

---

