---
title: "How to install Baldurs Gate 2 on Ubuntu?"
date: 2013-06-09
forum: Gaming &amp; Leisure
---

### Post by Karasawa7 on 2013-06-09
I have Ubuntu 12.04 and Wine 1.4.

I have 5 .Isos (CD1, CD2, CD3, CD4, CDToB)

I have written the 5 .isos To DVD-Rs.

Installation Meathod 1, Use extracted files.
It begins installation no problem. When it asks for CD 2 and I point to the folder, it instantly asks for CD3, then 4, then when I get to 5, says it cannot find it.

Installation Meathod 2, use ISOs via mounting.
I mount CD 1, installation begins per usual. When it asks for CD, and I point to the mounted CD2, it cannot find it. I should also note, when it asked for CD2, I tried unmounting CD1, then mounting CD2 in the same spot, same problem. Cannot find.

Installation Meathod 3, use CD's.
Insert disk one, installation begins per usual. When it asks for CD2, I insert CD2, and Ubunutu doesn't even do anything. Won't show up in my files or nothing. Same with CD3, CD4, and CD5.


I've seen/heard people being able to run this game. Am I missing something?

(Note: The .isos when mounted on windows worked just fine)

---

### Post by mastablasta on 2013-06-10
how are you running multidisk install? 

this is from Diablo2 for example: 
> For running the multi-disk install, it helps to run the install using the drive letter and to not switch your shell to the cdrom's path. For example: 
*~/.wine/drive_c$ wine "D:\setup.exe" (where D: is the assigned letter of your CD drive).* 
If you run while having a current working directory of /mnt/cdrom, for example, then you will lock the drive and you won't be able to eject the disk.


EDIT: also have you tried to install it with play on linux?

---

### Post by Karasawa7 on 2013-06-10
I'm running the multidisk install through the games installation process. CD's go though the CD drive (Oddly enough set to F by default) and I have ISO mounts that I can set to any letter of the alphabet. From my experience, playonlinux is useless. While it has baulders gate 2 there, it just opens up the baulder.exe file that I do manually.

---

### Post by oldrocker99 on 2013-06-10
I understand if you don't want to buy the game again, but GOG.com has the complete BG2 for $9.99, which is what the PlayOnLinux script installs, since it's currently the only way to obtain the game. I have it installed, running very well indeed, having installed it that way, since I have bought a lot of games from that site.

---

### Post by dmn_clown on 2013-06-10
> **oldrocker99 said:**
> I understand if you don't want to buy the game again, but GOG.com has the complete BG2 for $9.99, which is what the PlayOnLinux script installs, since it's currently the only way to obtain the game. I have it installed, running very well indeed, having installed it that way, since I have bought a lot of games from that site.

Gog is not the only way to buy that game:  [http://www.amazon.com/Baldurs-Gate-Collection-Shadows-Throne-Pc/dp/B00009ECGG](http://www.amazon.com/Baldurs-Gate-Collection-Shadows-Throne-Pc/dp/B00009ECGG)

To answer the question: [http://wiki.winehq.org/eject](http://wiki.winehq.org/eject)

---

### Post by oldrocker99 on 2013-06-11
> **dmn_clown said:**
> Gog is not the only way to buy that game:  [http://www.amazon.com/Baldurs-Gate-Collection-Shadows-Throne-Pc/dp/B00009ECGG](http://www.amazon.com/Baldurs-Gate-Collection-Shadows-Throne-Pc/dp/B00009ECGG)


Boy, am I embarassed; I didn't even know it was still available as a physical object, and I should have. GOG is still cheaper, and you get the game right away. Just sayin'.

---

### Post by Karasawa7 on 2013-06-11
Meh...I have the origional CD's that I turned into ISOs a LOONNNNNGGGGG time ago. The CD's have been used so much, they're pretty much worthless (Back when backing up CD's was possible, thank goodness I did).

I mean, I have a netbook with windows. And it's a netbook as in, SUPER TINY SCREEN, 1.67ghz single core, 1 gig ram. It actually lags out running BG2 in max settings. Max settings in BG call for like, 500mhz of processing power lol. Ahh well. I was really wanting to play it on my fancy shmancy big screen laptop with ubuntu. It would make sense that the GoG version would work, since it's been compacted into one single file instead of 4-5 .Isos. Bummer. 

I was hoping the remake of the first Baldurs Gate would have Linux support, nope. OSX and tablets got the port. Not us lovable linux users. Ah well....Changing status to solved, kinda.

---

