---
title: "Raid Questions"
date: 2009-02-24
forum: Desktop Environments
---

### Post by martied on 2009-02-24
Hi guys,

I have got everything working great in 8.10.

From video editing to office to internet to IM.

Only thing I have not got setup is raid

I have 2 x 250 gig HDD

Raid is not setup in Bios as i wasn't sure how to complete in linux.

If hardware raid is supported or software only.

Just wondering how I can setup raid 1 for data redundacy and backup.

Thanks

Marty

---

### Post by mr_muddle on 2009-02-24
Hardware RAID is 'supported' as it does everything in the hardware, you setup your RAID array in the BIOS of the RAID controller and it will work with any OS. You'll find you need to buy a card for this type of hardware RAID.

Most motherboards that have RAID on board are not true hardware RAID controllers. They use a combination of a software driver (mostly windows only AFAIK) and your computers CPU. This is often known as fakeRAID. This is most likely to be the situation you're in.

Software RAID is possible, and would be a much cheaper option than buying a true hardware RAID card. There's a how-to to be found here:
 [http://ubuntuforums.org/showthread.php?t=408461&highlight=raid+howto]("http://ubuntuforums.org/showthread.php?t=408461&highlight=raid+howto")

Hope that helps.

---

### Post by albinootje on 2009-02-24
> **martied said:**
>  If hardware raid is supported or software only.

Just wondering how I can setup raid 1 for data redundacy and backup.


Make sure you read about FakeRAID :
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

And this could be useful for your setup when you choose software RAID :
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

---

### Post by martied on 2009-02-24
Hi guys,

Thanks for your assistance. 

I will read up and go from there. I think I will just go software. Basically just after a mirror to protect my photos and things incase a drive fails.

Thanks again

Marty

---

