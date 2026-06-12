---
title: "2 Monitors Help"
date: 2007-11-30
forum: Desktop Effects &amp; Customization
---

### Post by dethredic on 2007-11-30
I am new to Linux and I have two monitors, a nVidia 8800GTS Graphics Card and only one screen showing stuff.

I am not sure if I have the latest drivers, or which ones I need, I read some posts and searched for twinview, but I couldn't really find anything, mainly because I don't really know what I am looking for. 

Thanks.

---

### Post by Happy_Man on 2007-11-30
try looking for a guide on setting up TwinView.

---

### Post by dethredic on 2007-12-01
Ok, thanks

---

### Post by NeilBlanchard on 2007-12-01
Hello,

If you are using the proprietary nVidia driver, then this may work:

in a terminal type "gksudo nvidia-settings"

then when it asks, type in your password

then use the X Server Display Configuration to set up the correct resolutions, refresh rates, and positions of your monitors.  I found that Separate X screen and Absolute positions allowed me to get my 3 monitors on 2 7600GS cards to work just right!

---

### Post by dethredic on 2007-12-01
> **NeilBlanchard said:**
> Hello,

If you are using the proprietary nVidia driver, then this may work:

in a terminal type "gksudo nvidia-settings"

then when it asks, type in your password

then use the X Server Display Configuration to set up the correct resolutions, refresh rates, and positions of your monitors.  I found that Separate X screen and Absolute positions allowed me to get my 3 monitors on 2 7600GS cards to work just right!

Wow, that works amazing!

---

### Post by dethredic on 2007-12-01
Ok, I am having some troubles setting it up.

I have it on Separate X screen, with Xcinima enabled, but It has the taskbars on the wrong screen (the bars on the bottom and top of the screen). They are on the one on the right, but I wan't them on the left one. 

This is probably due to my left screen being screen 1, and my right screen being screen 0, The only problem is I can't switch it.

Anyone know how I can do it?

---

### Post by Mostlyharmless42 on 2007-12-01
so i did this to enable my dual monitor, but now there is a long dely between when i click on something w/ a scroll down menu and when it pops up on screen 0.  When i turn off compiz, this goes away, and it also doesn't affect screen 1, which is the one i added.  I just seems like a kinda random symptom.  Does anyone know how to fix it?

---

### Post by BobCFC on 2007-12-02
> **dethredic said:**
> Ok, I am having some troubles setting it up.

I have it on Separate X screen, with Xcinima enabled, but It has the taskbars on the wrong screen (the bars on the bottom and top of the screen). They are on the one on the right, but I wan't them on the left one. 

This is probably due to my left screen being screen 1, and my right screen being screen 0, The only problem is I can't switch it.

Anyone know how I can do it?



If you click on an empty area of a panel you can drag the whole thing across to the other screen

edit:   this is what I do on twinview, I haven't used seperate X screens

---

### Post by skjoldfetter on 2007-12-02
with twinview i just get one wide screen... which is a pain because my monitors aren't right next to eachother...

and separate x screens wont work with both...

edit: got two separate screens by using the system > administration > screens and graphics

but if i set the screens to different resolutions it will scroll when i reach the edges of the smaller screen...

---

### Post by dethredic on 2007-12-03
Ok, i was playing around, and ud did some things / re did them, but now one of my monitors max resolution is 640x480!!!

---

### Post by dethredic on 2007-12-03
anyone know how to change this?

---

### Post by chm0d on 2007-12-03
You need to read on how to edit your xorg using twinview.  Google is your friend.  I run dual screens as well, and yea it took me alittle while to figure out what the heck to do, but after reading and googling I finally got it.  I can tell you that if you go to nvidia's site and search for twinview you will learn quite a bit.  Now if you want to be able to maximize an app to just one monitor you need to edit your xorg.conf and add what are called metamodes.  You will find what metamodes are on nvidias site when you search for twinview.  If you are new to linux be prepared to read and read some more.  I believe having to read so much to learn about the simplest things in linux makes people more afraid of it.  After you have passed that hurdle you are rewarding with one helluva OS.  I switched to linux 3 years ago, and I love not having to worry about virus', malware, spyware, and anything else that bloats winblows.

Chm0d

---

### Post by dethredic on 2007-12-03
I don't use twin view, but I will read up.

---

### Post by dethredic on 2007-12-03
Ok, well I found out that xinerama and compiz don't mix. When I change to twin view, it works, but my task bars are on the wrong screen. Can I fix this?

---

