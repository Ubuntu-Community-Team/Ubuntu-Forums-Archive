---
title: "Beryl problems"
date: 2007-03-17
forum: Desktop Effects &amp; Customization
---

### Post by isstern35 on 2007-03-17
hi everybody

Athlon mobile xp 2500++
Geforce 6200

i installed NVIDIA drivers using Envy  "driver version 1.0-9755"...after about 5 trys

now i installed beryl manager 0.2 and emerald
everytime i start beryl manager my borders disappear i have no beryl system tray and my terminal is all white
as for emerald 
trying to upload themes i get this message "Error calling .tar"
ive tried to reinstall emerald but nothing

also tried to mess around with the graphic drivers to reinstall and that messed my whole system up something with not being able to start GUI X server

for 3 days ive been installing and reformating my harddrive for this.
can someone please help me with this problem.

thank you

---

### Post by errhec on 2007-03-17
I think that you have the problem with your graphic card.
I have same problems ( with ATI ).., to return to logon ( from white screen) you should pres
 Ctrl + Alt + Backspace.
If your xserver does not start you should go to safe mode and type 
sudo dpkg-reconfigure  xserver-xorg 
and set the driver and mnitor corectly, you dont have to reinstall the whole OS :)
Err

---

### Post by isstern35 on 2007-03-17
lol yea i kinda figured that out at 6am just know
thanks any way
i had to config the source file for my card

---

