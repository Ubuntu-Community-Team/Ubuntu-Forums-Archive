---
title: "Screen resolution problem in Jaunty"
date: 2009-04-24
forum: General Help
---

### Post by AoA Linux on 2009-04-24
I have a Dell Inspiron 1525 running Ubuntu 8.10. I am using a 9.04 cd to mess around with it without installing before I upgrade, and I can not get my resolutions to fill the whole screen. Only the highest... 1650x1050 will take up the full screen. Does anyone know how to fix this before I upgrade to 9.04?

Thx

---

### Post by AoA Linux on 2009-04-25
Bump. I really want to upgrade to Jaunty, but need help with this screen issue.

---

### Post by CatKiller on 2009-04-25
I'm not entirely sure what you're saying. Are you saying that you can select different resolutions, but that your monitor stays in its native resolution and has the lower resolutions as proportions of the screen? With an LCD monitor this is fairly common. Non-native resolutions look bad on an LCD screen.

---

### Post by AoA Linux on 2009-04-25
No, I am saying when I choose anything but the highest resolution, the top and bottom OR left and right side of screen is letter boxed in black.

---

### Post by AoA Linux on 2009-04-25
Any help on this will be greatly appretiated.  I have experimented with 9.04 and all my stuff is supported very well, but letterboxing my screen is very annoying.

---

### Post by hatalar205 on 2009-04-25
I think you should add a screenshot to your post.

---

### Post by AoA Linux on 2009-04-25
Ok I shall get a pic of it.

---

### Post by AoA Linux on 2009-04-25
Ok guys.  Here are some pics of it letter boxing my screen...   this is on 1360x768 resolution, it does the same thing on all resolutions besides the highest.

Thx

---

### Post by AoA Linux on 2009-04-25
Has anyone seen anything like this before?  All the resolutions work fine in Intrepid?

---

### Post by AoA Linux on 2009-04-26
Bump.  Still in need of some help please.  Has anyone ever seen anything like in my pics with Jaunty?

---

### Post by CatKiller on 2009-04-26
Not seen anything like it, I'm afraid. If it was all the way round with the lower resolutions then there might be some hardware scaling thing in your monitor that you could turn on to have lower resolutions fullscreen but fuzzy. With it being either top & bottom or left & right, I have no idea what could be causing it. Weird that it doesn't do it in Intrepid, too. Have just upgraded to Jaunty myself.

My only suggestion for the time being, and it's quite a lame suggestion really, is just to leave it at the highest resolution so that it doesn't annoy you.

---

### Post by AoA Linux on 2009-04-26
Alright, thanks for the help catkiller.  Yes it has me stumped lol.  I started with 8.04 and have been using 8.10 for a while and neither of them had this happen.  Only thing that bothers me is at the highest resolution the txt is so small...

---

### Post by jaygo on 2009-04-26
you might find some options for screenscaling via software or hardware in the xorg documentation. Are you getting the black borders on the sides when you use, say, 800x600?

---

### Post by AoA Linux on 2009-04-26
I will see about that  thanks for the suggestion.

---

### Post by AoA Linux on 2009-04-26
Jay, I tried again and on the 800x600 resolution the black bars go to the right and left side of the screen and just become much larger.

---

### Post by CatKiller on 2009-04-27
> **AoA Linux said:**
>  Only thing that bothers me is at the highest resolution the txt is so small...

You can change the default font sizes. That might make the higher resolution more usable for you. System -> Preferences -> Appearance -> Fonts

Also, I found that when I was configuring my X server a while ago it had been given EDID numbers that made it calculate an incorrect DPI. That made the text much smaller than it should have been. If increasing the font sizes doesn't help, that might be something worth investigating.

---

### Post by AoA Linux on 2009-04-27
Thanks for the suggestion.  I have increased the font, panel, and icon size, and now it is very usable on the highest resolution and I have upgraded too 9.04 now.

---

### Post by jaygo on 2009-05-05
good news, and good choice. Photos & text will look much sharper by running at your screen's native resolution as well. Not to mention, you can see more of a photo than you would have at 800x600, etc. 

Also, you should mark this thread solved when you get a chance.

---

