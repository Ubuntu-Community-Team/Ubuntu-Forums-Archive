---
title: "Steam games on complimentary HDD: ext4 vs NTFS, noticeable difference?"
date: 2016-01-13
forum: Gaming &amp; Leisure
---

### Post by Dáire Fagan on 2016-01-13
In recent days I finally got around to wiping my (Windows 10 only) 250 GB SSD, and dual booting with the breath of fresh air that is Ubuntu 15.10. I am awaiting the release of Samsung's next generation M.2 NVMe 950 EVO, 1TB version, but until that time my linux /home partition is limited to 117GB, and Windows to 100GB. As anyone reading this sub forum will know, that does not leave much room for Steam to install games. Fortunately there is a program called Steammover that automatically creates symlinks on Windows for games if the user wants to move certain installed games to a complimentary HDD, and even more conveniently the linux version of Steam prompts us where to install each game. Yesterday I installed two old HDDs for this purpose, and once I have backed up any data I want to keep from them I want to wipe both of them to use for extra storage for media, not least of which Steam games for both platforms.

The HDDs are a 2TB Western Digital Green: WDC WD20EARX-00PASB0, and a much older HDD that came with a dell ~10 years ago, a Seagate Baracduda 320GB ST3320620AS (3.ADG).

My question is this, as just partitioning the whole 2TB HDD as one file system would mean I will not encounter an issue later where I will be wishing I made one partition larger or smaller, would there be any noticeable performance penalty playing Steam games while logged into Ubuntu if I formatted it NTFS? Or for best performance should I partition some of it ext4? I could also format the entire 2TB NTFS, while the older 320GB ext4, unless of course that drive is so old doing so would cost a noticeable hit to performance?

---

### Post by MikeCyber on 2016-01-13
ext4 should be faster than ntfs. google for phoronix tests. usb is also much slower than directly connected hds.

---

### Post by Dáire Fagan on 2016-01-13
Hi Mike, thanks fore the reply.

[Linux 4.0 Hard Drive Comparison With EXT4 / Btrfs / XFS / NTFS / NILFS2 / ReiserFS]("http://www.phoronix.com/scan.php?page=article&item=linux-40-hdd&num=1")

From the phronix benchmarks, it seems ext4 beats NTFS on all but one test which would bottleneck with SATA6.

Since I have now seen for myself how much better performance is on ext4, the question now is if I would still experience this if I say format the 320GB *old* Seagate Baracuda ST3320620AS (3.ADG) ext4? This would allow me format the entire 2TB NTFS, and use that for all the space Windows games are going to take up - any free space could then be used for music, video, etc.?

---

### Post by oldrocker99 on 2016-01-14
You shouldn't have any problems from running Steam games from an external drive; there will be longer loading times, however. Some external drives go to sleep and need a few thousand milliseconds to spin back up. You need an empty Steam directory for it to work, but you can add it to your Steam download destinations. 

+1 for ext4. There are ways to acess ext4 from within Windows:[https://askubuntu.com/questions/9933/how-to-read-ext4-partitions-in-windows](https://askubuntu.com/questions/9933/how-to-read-ext4-partitions-in-windows). I have, in my dual-boot days, successfully accessed ext4 partitions, and it was by using ext2read, a Windows program.

---

### Post by Bucky Ball on 2016-01-14
The older drive is probably 5200RPM. The WD Green uses a variable RPM which they say does reach 7200RPM speeds when required.

If drive speed is important in gaming, and I would imagine it is (don't game so don't know specifics), this may also be something to consider.

---

