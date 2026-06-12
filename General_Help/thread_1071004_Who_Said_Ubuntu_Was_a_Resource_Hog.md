---
title: "Who Said Ubuntu Was a Resource Hog?"
date: 2009-02-15
forum: General Help
---

### Post by JorgeMIlla08 on 2009-02-15
Heres Ubuntu After Boot, clean using just the necessary only 80MB of ram an a fully functional OS (Click On The Link)

[Ubuntu Screenshot # 1]("http://elodtw.bay.livefilestore.com/y1pMgObMCihm-aZwjGHvWrhkL7RoNeoPcgEyPYcWBGNLoPyfYhQyOd8EFWw27ZicSTuElVuOKZGR7gzfAgh4Jgwcg/Pantallazo_at_boot.png")

Heres Ubuntu After Openning a simple Image ( Notice the ram usage almost doubled)

[Ubuntu Screenshot # 2]("http://elodtw.bay.livefilestore.com/y1pXU2pkmMxlzclGCLrgHVVunkzbr_ICiJ6u7b3vjj6uEaK5h9lvgHY8jKb9a_wXp_RdP2s1Ecdy3hHNS6pTT6PJw/Pantallazo_image.png")

And Heres Ubuntu After closing the image ( Notice that ubuntu does not frees the RAM and it almost doubled its RAM usage after only openning an image 

[Ubuntu Screenshot # 3]("http://elodtw.bay.livefilestore.com/y1pzN-ww01nMbDhZS-SOiXKa1k35n1DXZO-m6KYX3UdZqMXwqDkWHIKBogwZIc1qkknRJwbOWXnozPIREgB9T20sA/Pantallazo_after.png")

My Question... Where is my RAM? and Why? 
People Often Criticize Windows For its "poor" RAM usage but it seems linux in general does it worse.

---

### Post by AlexBellisBrown on 2009-02-15
Thats unusual, is it just that one image? Or all images? Also, the photo is a bit meaty too, i dont know if thats caused this though. Its big (3400-2800) and just under 4mb.

---

### Post by sowelie on 2009-02-15
I am not sure why it doubles when you open an image. But after you close the image the os keeps that memory cached.

---

### Post by novafluxx on 2009-02-15
Yes its called caching, the system will use as much of your memory as possible before tossing it to the SWAP file/partition. This way when you go to open that ginormous image again, it'll load faster then it would  if it had to seek it off the hard drive.

If you're interested in changing the "swappiness" check out this FAQ

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Gramps on 2009-02-15
I just tried that on my system which has been running for awhile and before the picture opening it showed 435 mb (13%) I then opened like 5 3 mb pictures and it went to 513 mb started closing the pics and it went back to 435 mb. Be interesting see what it would be/do right after bootup.

---

