---
title: "My laptop is super slow ,  cpu consumption is crazy ?"
date: 2017-06-21
forum: Desktop Environments
---

### Post by aeid2 on 2017-06-21
spec is 
  - i5 
  - 8g of ram 
  - nvidia graphic card 

I can't literally play youtube (720p) videos in Chrome. 
CPU spikes to more than a 100% 

I'm not that experience with the operating system but I've enabled ( hardware acceleration in chrome ) and my graphic card seems to be working fine.

could somebody help me out!

---

### Post by gordintoronto on 2017-06-21
Did you install the video "additional driver"?

My system is much slower then yours (depending on which i5 your computer has) and I can play 1080P videos without problems. I'm using Xubuntu 17.04 and have the additional driver installed for my ancient 9400 GT video card.

A more detailed list of your configuration might be useful. Here is how I generate a detailed list:
cd Desktop
sudo lshw -html > config.htm

A file is created on my desktop, and when I double-click it, it opens in my browser.

---

