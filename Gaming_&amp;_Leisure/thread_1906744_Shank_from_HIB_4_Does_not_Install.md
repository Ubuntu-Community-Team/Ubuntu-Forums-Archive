---
title: "Shank from HIB 4 Does not Install"
date: 2012-01-09
forum: Gaming &amp; Leisure
---

### Post by TurtleKing on 2012-01-09
I tried downloading the 64bit .deb file twice, and still it does not work.

1st time: The connection would be interrupted half-way from their side (supermeatboy downloaded fine).

2nd time: The game downloaded, but Ubuntu Software Center will not install it

```
**Internal Error**
The file "/home/username/Downloads/shank_20111207_amd64.deb" could not be opened.
```

That has to be the most vague error report I ever had in Ubuntu.

Is there a known working version of the game for download? I really don't want to spend 4 hours downloading to find out again.:mad:

---

### Post by BcRich on 2012-01-10
> **TurtleKing said:**
> I tried downloading the 64bit .deb file twice, and still it does not work.

1st time: The connection would be interrupted half-way from their side (supermeatboy downloaded fine).

2nd time: The game downloaded, but Ubuntu Software Center will not install it

```
**Internal Error**
The file "/home/username/Downloads/shank_20111207_amd64.deb" could not be opened.
```That has to be the most vague error report I ever had in Ubuntu.

Is there a known working version of the game for download? I really don't want to spend 4 hours downloading to find out again.:mad:
Hi TurtleKing
sorry to hear that Shank isn't workin for you :(  but you can check the md5sum by cd-ing to the dir you downloaded shank to and 
```
md5sum name_of_shank_download_file
``` 

to verify that your downloaded file is not corrupted. Also I generally avoid installing .deb through Ubuntu Software Center and use GDebi Package Installer instead as it indicates the names of missing dependencies (if any), albeit one at a time. I hope you can get it workin cause it looks like a totally rockin game, it's also not likely that you will find another location to download the file from other than the location that supports your humblebundle key due to DRM and copyright.

---

### Post by TurtleKing on 2012-01-10
> **BcRich said:**
> it's also not likely that you will find another location to download the file from other than the location that supports your humblebundle key due to DRM and copyright.

No, I meant like are the bin or rpm file known to work well.

I will try Gdebi to see if it installs.

---

### Post by R33D3M33R on 2012-01-10
Why don't you use BitTorrent? It's faster, supports resume and it checks the file integrity automatically after it's downloaded. You can also click on the torrent version and "overwrite" your downloaded file. Your torrent client will automatically check the file and re-download only pieces that were corrupted.

---

### Post by Soulcage on 2012-01-10
I think I had this problem too I even checked the md5 it checked out.
So I used ```
sudo dpkg -i shank_20111207_amd64.deb
```

---

### Post by TurtleKing on 2012-01-24
> **Soulcage said:**
> I think I had this problem too I even checked the md5 it checked out.
So I used ```
sudo dpkg -i shank_20111207_amd64.deb
```

Thanks fixed it for me.:D

---

