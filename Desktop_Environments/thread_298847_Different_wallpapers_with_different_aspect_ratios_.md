---
title: "Different wallpapers with different aspect ratios for a dual monitor setup"
date: 2006-11-13
forum: Desktop Environments
---

### Post by Jonathan Métillon on 2006-11-13
Hi,

I have one screen with 8:5 aspect ratio (1680x1050) and one with 16:9 aspect ratio (1366x768). I don't use Xinerama, so each screen is independent.

But when I set a wallpaper on one of the screen, it is also applied to the other one. As the ratios are not exactly the same, the wallpaper is a bit stretched or a bit squeezed on one of the screen.

Is there a way to have individual wallpapers for each screen?

Thank you!

---

### Post by earobinson on 2006-11-13
what desktop manager are you using? Gnome? KDE? Xfce?

---

### Post by Jonathan Métillon on 2006-11-13
Sorry: I'm using GNOME 2.16.1 on Ubuntu 6.10.

---

### Post by Jonathan Métillon on 2006-11-18
Earobinson, any idea?

---

### Post by earobinson on 2006-11-20
I think this could be a gnome bug, but i'm not sure, works fine in xfce as far as I can tell. I look into it a bit more when I have time, anyone else feel free to contribute.

---

### Post by Jonathan Métillon on 2007-01-18
Earobinson, did you have time to look into that issue, or should I open a bug?

---

### Post by 5h4rk on 2007-08-30
Sorry for bringing this back, but I have dual screen and id like to know how can I set different wallpapper for each screen?

im not sure if im using xinerama or not, in fact, i have no idea what is it... :S :(

thanks

---

### Post by daynah on 2007-08-31
I'm not sure if this is the same problem as the other two but maybe if I post enough info to get someone's problem solved, it could help a similar but different issue.

So [here]("http://flickr.com/photos/daynah/1290092342/")  is a picture of the issue we are reaching, with what ever drivers, cards whatever we are reaching. They may not have ALL the problems I do but for sure some were mentioned.

To note in the picture... the Menu is on the left, everything minimizes to the left. Things that go to the center (not pictured) go right where the dividing space is. Basically, the comp doesn't realise it's two screens acting as one.

Alse in the pic, the background is of a land scape to demonstrate this, because one has to be higher than the other, the wall paper does go wonky. Worse happens when a singe screen wallpaper is used.

Now, this is how I got to this point, I'm not sure about the others. I have some cheap nvidia card. I didn't even mess with xorg, went straight to nvidia settings. I used twinview, leftof. I'm on Ubuntu Feisty.

Hopefully someone can help or point us in the right direction :)

---

### Post by ZeusABJ on 2008-04-26
Yeah I too am having this same issue. Unlike you Daynah I was somehow able to fix the issue of having my panels span across like that. I think I solved it by specifying a primary monitor in the nvidia-settings tool. TO be honest thought I messed with it so much I'm really not sure HOW I got that to work. Dual monitors in Ubuntu is such a pain. I was really looking forward to having this fixed in 8.04 (it was on the list of planned features). Really disappointed it did not happen. Here's hoping it makes it into 8.10. Hopefully someone out there has a solution for us.

BTW, I *LOVE* your usb hub. I have the same on one my desk!!!

---

