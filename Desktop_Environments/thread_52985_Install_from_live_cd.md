---
title: "Install from live cd"
date: 2005-07-29
forum: Desktop Environments
---

### Post by piper on 2005-07-29
How do you install from the live cd ? I can't get any of the install cd's to work, it just hangs at the "install  base system" at 17%, I made it once to 49%, I have burned 5 different cd's using 2 different burners, tried different speeds, always the same outcome, I have burned and installed 20 other distro's with no problems at all. I would really like to give Kubuntu a try.

8 gig harddrive, no other partitions
AMD k6-2 450
fic 503+ motherboard
Tried both TNT 2 Ultra and Matrox G400 max video cards
256 mb  ram

---

### Post by adwait on 2005-07-29
Try changing the method to disk at once rather than track at once.

---

### Post by piper on 2005-07-30
[QUOTE=adwait]Try changing the method to disk at once rather than track at once.[/QUOTE]
 Thanks for the reply adwait, however, I have done that, I ordered some cd's about a month ago, I guess I will wait another 2 months (sooner or later) when they arrive and try again, hopefully one of them will work. Thanks again for the reply :)

---

### Post by heimo on 2005-07-30
I'd try changing hard disk "access mode" in BIOS settings. Typically it can be LBA, Normal or Large. I'd also check the iso file with md5sum 

[https://wiki.ubuntu.com/VerifyIsoHowto?highlight=%28md5sum%29](https://wiki.ubuntu.com/VerifyIsoHowto?highlight=%28md5sum%29)
[http://ubuntuguide.org/#checkmd5](http://ubuntuguide.org/#checkmd5)
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

---

### Post by piper on 2005-07-30
[QUOTE=heimo]I'd try changing hard disk "access mode" in BIOS settings. Typically it can be LBA, Normal or Large. I'd also check the iso file with md5sum 

[https://wiki.ubuntu.com/VerifyIsoHowto?highlight=%28md5sum%29](https://wiki.ubuntu.com/VerifyIsoHowto?highlight=%28md5sum%29)
[http://ubuntuguide.org/#checkmd5](http://ubuntuguide.org/#checkmd5)
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)[/QUOTE]
 Thanks heimo, been there done that, I will wait for the cd's as I tried a third burner today, 5 differernt brands of cd's the oldest burner I have is almost a year old (plextor,yamaha,liteon). I guess kubuntu just don't like me :) I have been thru the basic's been building computers for over 25 years, thank you for the help. I just don't understand why this is the only distro I can't get installed, but it makes me more determined not to give up cause it won't install :) I just want to check it out and that is hard to do from a live cd.

---

### Post by heimo on 2005-07-30
:) No problem. What I'd do, is to download Ubuntu install CD and after install, do
 ```
sudo apt-get install kubuntu-desktop
``` 
Basicly, that's Kubuntu. Maybe Ubuntu install CDs will work better... *hopes*

Hmm... in your original post you speak about installing from live CD? I didn't know it's even possible. I thought those are only for booting and using from CD, not installing. Have you downloaded install CDs?

---

