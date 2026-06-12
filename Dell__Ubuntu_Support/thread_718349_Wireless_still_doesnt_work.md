---
title: "Wireless still doesnt work"
date: 2008-03-08
forum: Dell  Ubuntu Support
---

### Post by sm4n666 on 2008-03-08
So I just installed ubuntu 7.10.  i am using a dell 1520 with a "Dell Wireless 1505 Wireless-N Mini-card"
I went to [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) and followed the instructions there.  i get to step 4 and cannot do sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l ......this and my bluetooth are the only things that dont work.....the rest i got to work.....for my bluetooth other computers can see me but i cant see them and i cant share files...


any tips will be greatly appreciated

---

### Post by sanmeetkanhere on 2008-03-08
You dont need to do all that stuff to get your wireless to work. 

1.Just goto add/remove applications and make sure you have ndiswrapper installed.
2. Goto: 
[http://www.infdump.com/download-inf-files_new.php/inffiles/B/bcmwl5.inf/-/download.html](http://www.infdump.com/download-inf-files_new.php/inffiles/B/bcmwl5.inf/-/download.html) and download bcmwl5.inf.
3. Open ndiswrapper and click add wireless card, select the inf file you downloaded. It should detect the hardware as present.
4. click on the network manager icon top right and choose your wireless network.

Peace out,
Sanmeet

---

