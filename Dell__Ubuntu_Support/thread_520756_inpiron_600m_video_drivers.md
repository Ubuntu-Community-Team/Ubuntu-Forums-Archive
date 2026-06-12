---
title: "inpiron 600m video drivers"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by zaxor0 on 2007-08-08
I have a dell inspiron 600m with a ATI Mobility Radeon 9000. I am trying to have the VGA out work with my tv. I have the right cables and it works with a different laptop, but I need it to work with this dell. What video drivers would allow me to use the vga out? I almost works as of now with the "ati" (it says this in xorg) drivers. The screen recognizes the device but it does not display the screen. The laptop that does work has "radeon" drivers according to xorg, that laptop is using Sabayon v3.3. 

I believe that these "radeon" drivers might work, what drivers does radeon refer to? Is it the open source ati drivers?

---

### Post by Rocket2DMn on 2007-08-08
I was not able to get dual head to work on my 600m using an old digital flat panel, but hopefully you can have better luck since you're using VGA.
So here we go: 
[https://help.ubuntu.com/community/RadeonDriver#head-114acf2c1aad21944c3edcc63192e0ce40ac1323](https://help.ubuntu.com/community/RadeonDriver#head-114acf2c1aad21944c3edcc63192e0ce40ac1323)
I'm not sure if there is a difference between "ati" and "radeon", but this is the best place to start.  This guide has the setup for the driver, but I think you already have that.  You can start from the top if you want, but you should just be able to do the stuff for dual head.
Let me know how it works out.

PS: "fglrx" would be the restricted driver.

---

### Post by reckik on 2007-08-19
i tried to get the same thing working, but still no luck. As soon as i used the FGLRX drivers i always got the message "no screens detected"

with the radeon drivers everything works fine here, but i cant get the VGA working either, although it is detected by the atitvout tool.

did u have any luck?

---

