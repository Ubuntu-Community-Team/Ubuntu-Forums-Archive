---
title: "Testing Tips &amp; Tricks"
date: 2007-01-16
forum: Development CD/DVD Image Testing
---

### Post by pochu on 2007-01-16
Hello everybody!

I have done a list of all the tips you should know in order to test Ubuntu.

Here is the list. Enjoy it!
[LIST]
[*]First of all, you should know that here we work with the development version of Ubuntu, **so it can get broken easily.** So please, never use Feisty with valuable data. You can loose it.
[*] If you are new to Linux, you may want to have an stable system. If you want that, please use an stable release of Ubuntu.
[*]There are two types of CDs: Desktop CD and Alternate. The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 192MB of RAM to install from this CD. The alternate install CD allows you to perform certain specialist installations of Ubuntu.
[*]If you don't know the ID of your image:> **pochu said:**
> The ID is the number of the daily-build. When you download the daily-build, it is on a folder with the ID. For example, 20070111.1
[*]To check the md5sum of your image, open a terminal and write:```
md5sum imagename.iso
```It will return you some numbers and letters. If they are the same as those on the download page, the md5sum is right, and your iso is good.
[*]For bug reports, Ubuntu uses [Malone]("http://bugs.launchpad.net") at [Launchpad]("http://launchpad.net"). If you find a bug, please, [search]("https://bugs.launchpad.net/ubuntu/+bugs?advanced=1") if it has already been reported, and if it hasn't, [report]("https://bugs.launchpad.net/ubuntu/+filebug") it yourself.[/LIST]
That's everything I have to say now. I will add things whenever I remember them :D

Regards and good luck with your tests!
Pochu

---

### Post by spd106 on 2007-01-18
When it comes to the days just before release the cd images can change quite rapidly as fixes are applied. I have found rsync and jigdo/bittorrent to be two useful tools.

**Rsync**
You use rsync to update a desktop iso since it only transfers the changes. Check out [https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage) for a simple introduction.

**Jigdo**
Jigdo is useful for the alternate iso as it allows you to download just the packages that have been updated. See [https://help.ubuntu.com/community/JigdoDownloadHowto](https://help.ubuntu.com/community/JigdoDownloadHowto)

**BitTorrent**
If you have a partial image and want to finish it off, say jigdo failed with the last few packages, then you can use bittorrent. See [https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent). I recommend bittornado over the standard client.

While bittorrent is great for removing load from the servers, if no-one is on it seeding then you won't get anywhere. It might be a good idea to promote seeding of torrents for the cd/dvd testing team. As long as every one moves to the newest when it comes online.

---

### Post by Henrik on 2007-01-19
Thanks to both of you! Very useful info. (which I will integrate in the how-to when I get a spare moment ;) )

---

