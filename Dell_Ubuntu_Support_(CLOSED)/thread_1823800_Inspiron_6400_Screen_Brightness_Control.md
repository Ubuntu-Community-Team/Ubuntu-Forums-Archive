---
title: "Inspiron 6400 Screen Brightness Control"
date: 2011-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MARP1961 on 2011-08-12
My son's Dell laptop has a strange issue with screen brightness. We can alter the brightness using the fn key with the up and down arrow keys but it will not go anywhere near full brightness. It seems to have only three different settings and they go up in odd steps eg. Dim, Brighter, Brightest, Dim, Brighter! 

The maximum setting is not maximum brightness and maximum is not very bright anyway (I'm guessing about 30%). This means we have to use it in a dim room.

It is a dual-boot and the same problem exists in Vista also. I've checked BIOS settings and brightness is set to maximum in both AC power and battery modes. Interestingly, the BIOS setting seems to make no difference to this behaviour.

Something seems to be preventing full brightness. Any ideas? I know things are often possible in Ubuntu that are not in Windows.

---

### Post by hypertyper on 2011-09-20
I've just spend days on playing with brightness and what I would try in your place was install ubuntu tweak and look at the brightness settings there. 

gconf-editor -> apps -> gnome-power-editor -> backlight 

gives you access to the same options if you prefer.

There are other approaches, setpci and xbacklight which you can have a google for. None of those worked on my Samsung but might work for you. xbacklight seems quite common.

If you are having the same problems in Windows then I would assume it's a hardware problem though.

---

### Post by MARP1961 on 2011-09-30
Thanks for those suggestions; but it now seems that an incompatible screen was fitted at some stage and this causes the screen brightness range to be reduced.

---

### Post by ashrich on 2011-10-10
Don't forget that there is a brightness control in the bios on the I6400 , it allows you to alter the screen when on mains and/or battery 

     Ashley

---

### Post by MARP1961 on 2011-10-10
Thanks for that, but I played around with BIOS settings many times only to find the problem remained.

I have now solved the problem by replacing the screen/inverter combination with one removed from a lately working Inspiron 6400. The screen brightness features are now all as normal!

After quite a bit of reading it appears that some screens will simply not work correctly in Dells. The screen's actual firmware does not allow full brightness control from the Dell motherboard.

---

