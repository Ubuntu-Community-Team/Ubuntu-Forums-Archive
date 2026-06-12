---
title: "Noob - Help With resolution"
date: 2011-06-11
forum: Desktop Environments
---

### Post by emgineering on 2011-06-11
Hello. I'm a noob at linux, just downloaded 2 days ago and I'm overwhelmed with the amount of information out there.... 

I hooked up an old tv to my old desktop, and my old tv has these horizontal lines at the top. What I want to do is resize the screen so that my screen is below the horizontal lines, I don't need to use that top part of my tv screen.

Anyway, I tried reading about xrandr and what not, but don't understand what to do.  When I run xrandr -q I get this: 

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 

So, I understand I need to add more resolutions and something about a config file..... but like I said this is way over my head. Can someone help me out and guide me so that I can fix this?? Thanks a lot!!

---

### Post by jarrah-95 on 2011-06-11
from the sounds of what you just said, you want to move the picture down below the lines in the screen? 
it easiest way to do that is to use the menu on the tv, to change the position of the picture, an then re-size it. i cant explain it here in detail as all tv's are different, but if you go into the menu, then picture, it should be quite simple. 

hope this helps

jarrah

---

### Post by emgineering on 2011-06-11
thanx for the response! 

I tried doing that. For some reason, my tv wont move the screen much at all just a few centimeters and wont resize.... its weird.... hahaha that's why I was trying to do it within ubuntu.

---

### Post by emgineering on 2011-06-12
Bump....

Anyone with any other ideas?? 

and while I'm here, does anyone know why my video streaming would be choppy? I have an intel corporation 82845g gl graphics card, 1 gig ram, 2Ghz processor, pentium 4. Flash videos are a bit choppy, even after I let the video fully load. Have the latest flash player and have the flash player add on for firefox. 
Does this mean i need a new graphics card? and if so what type of (cheap) graphics card can i get?

---

### Post by emgineering on 2011-06-13
Bump again....


Soooooo..... anyone have any ideas??? or is there anywhere else you can recommend for me to ask this??

---

### Post by nzjethro on 2011-06-13
Check out this.

[http://ubuntuforums.org/showthread.php?t=77257](http://ubuntuforums.org/showthread.php?t=77257)

May be on the right track. I'll keep an eye out for something too.

---

### Post by emgineering on 2011-06-14
Thanks for the help! 

I see that this might work..... but, before I do anything..... I get a different screen than what the guy on the post has. 

When I run xvidtune, I get this:

"Vendor: (null), Model: (null)
Num hsync: 0, Num vsync: 0"


I don't get all the 
[FONT=monospace]
Horizsync
Vertrefresh etc.

Sooooooo, should I just ignore that and keep going, or what should I do?

[/FONT]

---

### Post by nzjethro on 2011-06-15
Did you check out [this]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21") sub-thread?

I'm not sure what to make of that error. If you've backed up your xorg, maybe just ignore it and see what happens. If you cook the system worse, just restore your xorg.

---

### Post by emgineering on 2011-06-15
Hmmm I dont think I have a xorg file... when I try to back it up it says that file doesn't exist?? haha

---

### Post by emgineering on 2011-06-15
Hahhaa I think i'm giving up, I tried looking on how to make a new xorg.conf file but I'm too noob at this and without step by step instructions I don't think I can do this hahaha. Thanks though!

---

### Post by nzjethro on 2011-06-16
Rough. If I see anything that may fix the issue in my trawls I'll pm you the details. And if you find anything, jot it down here for future reference.

---

