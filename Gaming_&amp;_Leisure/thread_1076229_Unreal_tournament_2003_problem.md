---
title: "Unreal tournament 2003 problem"
date: 2009-02-21
forum: Gaming &amp; Leisure
---

### Post by Sylos on 2009-02-21
hello all,

I recently had a problem getting UT GOTY 99 to run natively in linux so I decided to buy UT 2003 as it has the linux installer sh script on it. Unfortunately, after much post reading and jiggery-pokery I have arrived at the same place as I arrived with GOTY. I got it installed but when I try to run it it doesnt go full screen. The video bit where the bot jumps through the logo comes up, I press Esc to get to the menu and the mouse wont work leaving me with the only option of exiting. The terminal in the background reads:

fcntl:operation not permitted
fcntl:operation not permitted

Any help would be very much appreciated as I am itching to get back to the online frags.
Thanks...

---

### Post by R33D3M33R on 2009-02-22
Read here: [http://ubuntuforums.org/showthread.php?t=52164](http://ubuntuforums.org/showthread.php?t=52164)

Try to use sudo

---

### Post by Sylos on 2009-02-23
Cheers for the reply.
I have read the post and after some other fiddling have got the game working....sort of.
In my usual hadry heron distro the game now starts but the menus have white vertical lines through them that make it very hard to see the oprions. Once the gameplay starts the graphics are ok but it crashed after about 10 minutes.
So, I had the idea of reinstalling Gutsy 7.10 cos I ran UT99 on that without problems. So i got that set up with the NVIDIA driver from their site and installed the game. Now I get the same fcntl:.... error but the menus appear normal and the game runs ok ......... for around 15 mins and then it stops being full screen and freezes the keyboard and mouse input. The game keeps goin in the smaller window but I cant control it. I have to ctrl_Alt_BKSP to log out.
when this happens the terminal output is 

fcntl: operation not permitted
fcntl: operation not permitted
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

I checked the NVIDIA file for the driver I installed and it says it supports the s3tc. I tried following some other threads about 2004 that suggest stopping esd sound but when i try the "killall" command it just returns "no prcoess ended" or something to that effect and the game still crashes. Im gonna try writing a bash script to stop esd and run ut2003 but I'm doubtful if it will work.
Any further advice gratefully received.
Thanks

---

### Post by R33D3M33R on 2009-02-23
Try this:

Find the /usr/lib/libSDL-1.2.so.0 (or later) file and save it to the your ut2003/System folder. May I ask what graphics card are you using and what drivers?

---

### Post by Sylos on 2009-02-23
I have an NVIDIA Geforce FX5200 card with the NVIDIA-Linux-x86-173.14.12.pkg1.run driver straight from the nvidia site on Gutsy 7.10. My hardware is pretty old, a compaq pressario with an AMD Athlon processor.
I assume you mean find that file and copy and paste it into the ut2003/System folder so that the engine can find it. Sorry if thats a stupid question but Im pretty knew to the linux world.
Thanks very much for the help.

---

### Post by R33D3M33R on 2009-02-24
Yes, that is correct. Also, your hardware should be good enough to run the game.

---

### Post by Sylos on 2009-03-04
Thanks for the help but I'm afraid it hasnt worked. When i copied the LibSDL file across it siad ti was already in the system folder. I replaced it anyway but the problem persists. 
Having done some more reading around on the web I have found a few posts suggesting that the XiG.... message is actually benign and wouldnt cause any problems. From what I can make out XiG is Xorgs commercial accelerated graphics driver and doesnt ship with ubuntu. Therefore the message has little meaning and shouldnt affect things. 
Im thinkng perhaps this is an internal game error that Im getting. 
Im going to try and get the game log and see what it says when it crashes.
I shall post any solutions I find. In the mean time any further guidance or  thoughts would be gratefully received.

---

### Post by Sylos on 2009-03-08
Ok, I appear to have stumbled upon the source of the problem and the solution. Ubuntu automatically has the screen saver set to kick in. I disabled this and the game now appears to run without having any problems.
Such a simple problem and fix.
Thanks for all your help.

---

