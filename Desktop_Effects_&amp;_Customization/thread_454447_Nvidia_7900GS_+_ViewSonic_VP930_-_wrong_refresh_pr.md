---
title: "Nvidia 7900GS + ViewSonic VP930 - wrong refresh problem"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by AkumA on 2007-05-25
Hi!
I've just installed Ubuntu 64Bit and i've enabled Desktop Effects. Everything is working fine except monitor's refresh.

Monitor refresh is perfect with "nv" driver.. but with "nvidia" driver enable there's no way.

My VP930 should reach 75Hz and with my old PC (With GeForce 2, Ubuntu Feisty and XGL), after i've entered HorizSync and VertRefresh manually, worked without any problem.

When i use nv i can set 75hz without adding the HorizSync and VertRefresh to xorg.conf.. while when i install nvidia driver they becomese necessary to see in a decent way my desktop.. but frequencies on Gnome are wrong!

Now the frequency is 50 or 56 and I've tried a lot of stuff:

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

I don't think i've skipped something.. i think i've tried all these solutions but no one worked for me.

Setting frequency with nvidia-settings changed nothing (Except keyboard settings and other stuff :P bleah!) and while i've tried few thing i've obtained only other frequency options.. like 50 - 56hz, 50 55 57 hz and stuff like this.. but  not 60 - 75 hz as i could easily get on my old PC

---

### Post by dabl on 2007-05-25
Did you try > nvidia-settings in a console window, to bring up the Nvidia driver utility?  On that menu, choose "Xserver Display Configuration" and then you can play with the refresh, within the limits that the driver will allow.

HTH :)

---

### Post by AkumA on 2007-05-26
> **dabl said:**
> Did you try  in a console window, to bring up the Nvidia driver utility?  On that menu, choose "Xserver Display Configuration" and then you can play with the refresh, within the limits that the driver will allow.

HTH :)

Already tried.. doesn't change anything

> Setting frequency with nvidia-settings changed nothing (Except wrong keyboard settings and other stuff :P bleah!) 

---

