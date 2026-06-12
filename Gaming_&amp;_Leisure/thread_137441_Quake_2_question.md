---
title: "Quake 2 question"
date: 2006-02-28
forum: Gaming &amp; Leisure
---

### Post by Justbill on 2006-02-28
Hello All,
I will try to keep this introduction short! My name is Bill Sanders, I am from House Springs Mo. U.S.A. I am a 47 year old cabinet maker ( so go easy on me with all the computer jargon), and am new to Ubuntu\\:D/  My experience with computers is limited to the last 2 years when I got my first box, an old HP Vectra 233 with win 98 on it (now retired!). I since have gotten a new Compaq with 2.93Ghz penium 4, 512 ram ,so on and so on. And this HP with a 500 Mhz Celeron and 256 ram. The Compaq is dual booting win XP (which we never use) and FC4, the HP has Ubuntu by itself! I am still obviously cutting my teeth on linux, FC4 was a nice start, but , the rpm's kind of drove me nuts, ao here I am!
I will have plenty of questions in the future , however my first ones do pertain to games, so here we go.

1). I used Synaptic to install Quake 2, I have since learned that I need to have the game on a cd in order to install the maps and such, I don't have the game Quake 2 on cd, and am not able to find a copy in stores ( because it is an older game). Can anyone direct to a web site where I might purchase the game Quake 2, in a download, or, are there any other alternatives? Say the originall Quake? Will those files work in Quake 2?

2). My second question for now would be, where might I find information as to which video cards are supported in Ubuntu. I am going to put it in the HP box (500mhz celeron, 256mb ram) I have a hp pavilion mx50 monitor on this machine, any suggestions?

Thanks much for taking the time to read this, I know I will have more questions in the  future, this is somewhat different from fedora core, but I can already tell I like it better.

Thanks
Justbill

---

### Post by brynjarh on 2006-02-28
1) You could use the data from a shareware version of Quake 2, the easiest way would be to do **sudo dpkg-reconfigure quake2-data** and choose "download shareware data".

2) To my knowledge GPUs from NVIDIA work best with Linux. [http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver]("http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver"). I don't know of a list of supported video cards/GPUs but GPUs from NVIDIA are known to work.

---

### Post by Justbill on 2006-02-28
THANKS ALOT!! Brynjarh!

That got the game working for me. And thanks for the link on installing the video cards!

Thanks again
Justbill

---

