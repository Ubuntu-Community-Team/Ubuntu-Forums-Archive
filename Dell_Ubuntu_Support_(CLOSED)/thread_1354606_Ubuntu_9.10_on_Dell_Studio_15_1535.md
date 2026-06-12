---
title: "Ubuntu 9.10 on Dell Studio 15 1535"
date: 2009-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vigos on 2009-12-14
Hi all,

I had Ubuntu 9.0.4 sucessfully installed on my dell 1535 laptop.

However I wanted to upgrade to 9.10 so my plan was to do a fresh install. So I downloaded the ISO image, I checked the MD5 checksum and everything appeared ok.

However when I booted from the cdrom and selected "Install Ubuntu" it just seems to hang and the keyboard became unresponsive.

I just want to know if anyone else managed to install this sucessfully on a dell studio 15 1535 laptop?

Thanks

---

### Post by v1nsai on 2009-12-14
I couldn't get the desktop iso to boot on my Studio 1555, I ended up downloading the alternate installer and doing it like that.  You might also try booting with the 'noapic' and 'nomodeset' options, I need both of those options to boot my installed 9.10.  All in all 9.10 works a lot better out of the box than 9.04, don't be discouraged I would definitely make this upgrade.

The extra configuration info you need after installing can be found [here]("https://wiki.ubuntu.com/LaptopTestingTeam/DellStudio15_2") and [here]("https://wiki.ubuntu.com/LaptopTestingTeam/DellStudio15").  I've been able to get everything working flawlessly, except for the intel graphics driver (lshw -C display still shows my displays are unclaimed), I've got a thread [here]("http://ubuntuforums.org/showthread.php?t=1336421") trying to figure that one out.

---

### Post by clevertomato on 2009-12-14
@v1nsai: My Dell Studio 1555 will arrive in a couple weeks (with ATI 4570). Thanks for the links to the pages for this notebook. Should I expect to run proprietary ATI drivers on this, open source drivers, or do both work? How can I get more info about what drivers work with the ATI 4570 and the pros / cons of different drivers for this ATI GPU?

---

### Post by v1nsai on 2009-12-14
The links I gave you to the Dell Studio 15 ubuntu wikis probably have the information you need about the ATI drivers.  The wikis have all the info you need about a particular system in one place.  I don't have the ATI card in mine so I don't know.

---

### Post by vigos on 2009-12-14
> **v1nsai said:**
> I couldn't get the desktop iso to boot on my Studio 1555, I ended up downloading the alternate installer and doing it like that.  You might also try booting with the 'noapic' and 'nomodeset' options, I need both of those options to boot my installed 9.10.  All in all 9.10 works a lot better out of the box than 9.04, don't be discouraged I would definitely make this upgrade.

The extra configuration info you need after installing can be found [here]("https://wiki.ubuntu.com/LaptopTestingTeam/DellStudio15_2") and [here]("https://wiki.ubuntu.com/LaptopTestingTeam/DellStudio15").  I've been able to get everything working flawlessly, except for the intel graphics driver (lshw -C display still shows my displays are unclaimed), I've got a thread [here]("http://ubuntuforums.org/showthread.php?t=1336421") trying to figure that one out.

ok thanks I'll try the alternate installer. I've already tried before the noapic option but didnt work for me either

anyway I'm going to download the alternate iso image now and try it out

---

### Post by vigos on 2009-12-14
Ok now posting this from Ubuntu 9.10, thanks for your help the alternate cd worked great. 

Have still to setup wireless card and graphics card but should be similar to what I had to do for 9.0.4 thanks again!

---

