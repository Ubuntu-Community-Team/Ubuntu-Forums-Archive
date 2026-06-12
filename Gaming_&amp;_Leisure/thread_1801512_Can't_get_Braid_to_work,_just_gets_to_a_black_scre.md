---
title: "Can't get Braid to work, just gets to a black screen and stays"
date: 2011-07-10
forum: Gaming &amp; Leisure
---

### Post by Funkin'Funkin' on 2011-07-10
Hey guys. Long time user, first time poster, and I will probably always support ubuntu! And I plan on helping out on the forums!:popcorn:

However, recently I downloaded Braid from the Ubunutu Software store, and everytime I start it up, it goes to a black screen. The mouse cursor changes to black with a white outline (which I assume its the mouse cursor in the game). I have a feeling its running, but I dont know where to find the program to edit the options and I don't know how to get it to stop having a blank screen.

Anyone else have this issue?

---

### Post by Saxon47 on 2011-07-16
Hey,

I am having the same problem on my machine, which is an Asus 1215n. At first, I thought it was another problem with Nvidia Optimus, which Linux has given me no end of problems. Would you happen to have a similar system, or just a straight up dedicated card?

---

### Post by Funkin'Funkin' on 2011-07-16
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

That's mine, Dell latitude d620, corde duo proc, 4 Gigs ram... 11.04 Natty with Unity (unity shouldn't matter, it's freakin' great when you configure it right).

I heard about resizing the window through the options in command line, but I can't even seem to find that...

anyone have ANY suggestions? People without the highest powered, biggest display machines shouldn't miss out on this classic!

---

### Post by Saxon47 on 2011-07-16
I just know that when I enter the command 'optirun64 braid' (Bumblebee allows Linux to utilize the Nvidia card), it starts up and then says: 'exec: 301: braid: not found. That is when I try the terminal, anyway. When I click on the icon in the applications folder, it just sits there with a black screen and does nothing else.

---

### Post by Funkin'Funkin' on 2011-07-16
Well, how do you run it from a terminal? there has to be a way to get some options that will run on our machines.

---

### Post by Funkin'Funkin' on 2011-07-16
it's in the /opt/braid folder... you can use the following as posted from the braid website

-language X  (where X is one of: english, german, french, italian, spanish,  portuguese, japanese, korean, tchinese ...right now it's always  defaulting to English, but a future build will try to make an  intelligent choice based on environment variables.)  This changes the language the game's text appears in.  -windowed  Makes the game windowed, instead of fullscreen.  -vsync -no_vsync  Try to force or disable sync to vblank. Prevents tearing, if your video  card can keep up. If your framerate is bad, tearing might be an  acceptable tradeoff.  -no_music  Disable music.  -half  Reduce rendering to half...makes game look worse, but could make a big  performance difference on slower GPUs.  -60fps -30fps -20fps -15fps  Try to keep the framerate at 60/30/20/15 frames per second. Might be  useful on a slower machine to try to push the system less at a tradeoff  of less responsiveness and smoothness of animation.  -width X -height Y  Specify size of window (or fullscreen resolution). -width 1024 -height  768 will make a 1024x768 window.    ...there are a few others, but those should cover what most people care  about.




and the option -no_post will make it look glitchy as hell, but its still playable

---

### Post by Saxon47 on 2011-07-18
It still does not work for me. Everything is where it should be, as far as I can tell. When the game loads, I cannot do anything, even open a terminal. An interesting observation, however, I changed my unity theme, then I went for another round with Braid. This time, instead of a black screen, I get a partially rendered window, its translucent, the desktop is all there, and the clock freezes on the time I opened the game.

I almost want to say that the game may be too much for this little trooper of a computer, but when I was running Windows, I could run C&C Generals, Plants vs Zombies, the first Splinter Cell, even! Linux shouldn't have that large a graphics foot print, should it?

---

### Post by neilj05 on 2011-08-18
Same issue here...do i get a refund?
So looking forward to playing it too!

Anyone has got this game working? Any insights?
PLEASE !!!!

---

### Post by Elfy on 2011-08-18
Thread moved to Gaming & Leisure.

---

