---
title: "Latest m1330 version of Ubuntu anyone?"
date: 2008-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Phoneyakk on 2008-08-01
Can you download the version of Ubuntu that ships with the Dell xps m1330. I may have incorrectly phrased my question due to a lack of tech savvy, however you probably understand what I mean. Can I download a file containing the form of Ubuntu Dell opted for, as well as the drivers and specific setteings the m1330 requires. 

Having waited for my brand-spanking new m1330 for much longer then I would wish upon even my worst enemy, it stung to learn that Ubuntu would be shipping on the m1330(a better product for less money, who dosent love that).

I was less then surprised when dell.com offered me no help in finding what I wanted, imagine a company being less then extatic about open source software. (Go to Dell.com and try to purchase an m1330 as if your were their average consumer, there is little chance you would learn of, let along buy a laptop with Ubuntu. It's not a choice when configuring your laptop, and in  my experience you must keyword search for "Ubuntu" to ever find that section of their website) To Dell's credit at least they're offering alternatives to Windows. 

I am more then ready to Give Ubuntu a spin, but I would rather start as well prepared as is reasonable, rather then jumping in to soon and getting in over my head.

If the techniciana over at Dell have ironed out the creases in Ubuntu on an m1330, why should I make it any harder then it need's be.

Feel free to add any insight you find usefull in your comment, I certainly could use the help. Moreover, How do you feel about Dell's marketing of Ubuntu, is it good, is it bad? Should they make the option more public, or should they be profiting of Ubuntu at all? -Share you point of veiw, and thank you for your help.

---

### Post by Temposs on 2008-08-02
Hi Phoneyakk. I'm glad you want to try Ubuntu :-)

I think Dell hasn't gotten around to posting their particular fiddling with the most recent Ubuntu 8.04(hardy heron)

However, they do have their version of Ubuntu 7.10(gutsy gibbon) available to download here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

7,10 is also a fabulous version of Ubuntu, so you should enjoy it just as much. It's supported until April 2009. By then, I think, Dell will have updated their wiki site to include a download for the current version of Ubuntu.

Once you download the correct file for your particular machine, you'll want to follow the instructions here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

EDIT: After you install the Dell Ubuntu version 7.10, you may optionally go here: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04) . That webpage will guide you in upgrading to Ubuntu 8.04. I'm not sure how upgrades are with Dell Ubuntu, but it could be that if you upgrade, you'll may still only have the Dell customizations done for Ubuntu 7.10. But don't quote me on that!

I am happy that Dell is offering Ubuntu pre-loaded computers. Since I do tech support for my Mom, it makes it easier on me for her to use Ubuntu, which is why I just helped her purchase a new Dell 1525N.

I think that unfortunately, Dell is hindered in their ability to market Ubuntu by some creative licensing agreements with Microsoft that gives Microsoft a guaranteed front page on their website. I'm glad you've found your way around that. Since Dell must make their deal with Microsoft to stay in business, they are forced to marginalize Ubuntu. The more people use and buy Dell Ubuntu, the less incentive they have to stick to Microsoft's oppressive contract.

If you have any more questions, hopefully the folks around here will be able to help you.

---

### Post by TimDaniels on 2008-08-19
Although the downloadable .iso file for Gutsy 7.10 is a true installation file, the recently available .iso file for Hardy 8.04 is a factory recovery file, i.e. it will obliterate the entire disk and then create:
1) a partition containing diagnostic utilities,
2, a partition containing a recovery image of what you will have installed,
3) the Ubuntu installation itself that fills up almost the entire disk,
4) a swap logical partition within an Extended partition.

If you want to set aside a partition for /home, or if you want to dual-boot with another OS, you're SOL.

As for an upgrade from 7.10, I tried that and I wound up with problems with the nVidia driver and a way-too-complex xorg.conf file that never did let my Dell Bluetooth Travel Mouse work right.

What works best is to just download the 700MB 8.04 installation file from the Ubuntu website and install 8.04 from scratch.  The installation goes easily, just like the 7.10 installation from Dell's website, and you can make separate partitions and you can put Grub in the Ubuntu partition if you want another OS's boot manager to get first control.  You'll find the nVidia driver and the Broadcom driver listed in the Hardware Drivers dialog box, and just enable them to make them work.  My Bluetooth mouse didn't work at first, but I found that the "Configured Mouse" wasn't included in the ServerLayout section of /etc/X11/xorg.conf, so I added that one-line entry and then the Bluetooth mouse worked.  It's a piece of cake if you just ignore Dell for Ubuntu 8.04.

*TimDaniels*

---

