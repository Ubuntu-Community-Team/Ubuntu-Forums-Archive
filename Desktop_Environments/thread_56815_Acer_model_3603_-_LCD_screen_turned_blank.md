---
title: "Acer model 3603 - LCD screen turned blank"
date: 2005-08-14
forum: Desktop Environments
---

### Post by ongcoo on 2005-08-14
I am trying to install Ubuntu in the above notebook but it turn to blank. halfway thru
I understand we need to edit a folder /etc to change the video setting.
Can anyone direct me how to do it.
Thank you
Ongcoo

---

### Post by sml on 2005-08-23
Save the hassle of editing /etc/X11/xorg.conf and just run
#xorgconfig   
or
#sudo dpkg-reconfigure xerserver-xorg

I had success using the rates 31.5-50 and 40-90. And I just used the vesa driver.

Also dont forget to use the 855resolution to et the correct resolution (i really don't know why they dont rename the file because it is also designed to work with the 915 chipset on your 3603 laptop.)

Good luck with the wireless! I failed. I think i had everything perfect with both ndiswrapper and also later with linuxant but could just not turn the wireless card on!  :( There is a acer app to control the card on certain acer models. I didn;t have much success with it on the 3603.

Apart from that it was all easy.

---

