---
title: "Need help with Beryl/World of Warcraft setup?"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by Full-choke on 2008-01-20
First off, new to the forums and hope everyone can help me!  I have been running Ubuntu for about a year now and been on 7.04 since this summer.  So I am fairly familiar with the whole thing.  I have been trying to set up WoW with the use of Wine.  I feel I am very close but I keep getting an error about not being able start 3D Acceleration.  In my searches for an answer I found using Beryl as a solution.  But here's the deal...I can't get it to set up right.  Every time I run the manager the screen flashes a few times and then it's back to normal.  It will not switch over to run Beryl, it stays on MetaCity.  I can however get it to stay on Compiz which is another option.  Any help on getting Beryl going would be helpful.

Thanks a bunch,
F-C

---

### Post by Hairy_Palms on 2008-01-20
sounds like you need to install your graphics driver, if you open a terminal and type

glxinfo | grep direct

it should say

direct rendering: Yes

what graphics card do you have?

---

### Post by Full-choke on 2008-01-20
Okay, strangely enough...my response is "NO".  The odd thing is that just yesterday when I was working on installing WoW it said yes.

The first step to the whole thing was "glxinfo | grep rendering" which yesterday morning read "YES"...and now it doesn't.  I'm so confused :(

---

### Post by gspat on 2008-01-20
So then your main issue atm is you don't have graphics acceleration on.

I take it you already have WoW installed, so that step is already done...

follow the tutorials for your graphics cards to get that running now, maybe even look in /etc/X11 to see what has changed since yesterday in your xorg.conf.

Once you fix that, you should be good to go.

WHat GFX card do you have? My nvidia gave me lots of grief until I got the xorg.conf file issue settled.

---

### Post by Full-choke on 2008-01-20
Well, I have an onboard chipset, made by ATI.  It is pretty good and will do what is required for the game.  

As far as the whole /etc/X11...a lot of things changed yesterday.  My father (who is my mentor and teacher, so he knows his stuff) tried working on it yesterday.  We made a backup of our good conf file to resort back to and we got another driver.  The problem is that when we installed it we would lose all window control, all I could run in was basically terminal.  We changed everything back to the old conf, but apparently something didn't take.  Maybe that's what is hacking me up?

Under my hardware info it says the following: 
Vendor: Intel Corp.
Product: 82945G/GZ Integrated Graphics
OEM Vendor: ABIT Computer Corp. 
OEM Product: Unknown (0x1086)

Where could I find the proper driver for that and try to get things installed and going?

Thanks again,
F-C

---

### Post by gspat on 2008-01-20
if I recall correctly, ati worked best using aiglx, so check your older xorg.conf files for that and find one with settings  that worked. but you have an intel chipset.

a quick way to check if it worked is to just try to run glxgears... just type glxgears int the terminal.  if you get the gears running and it shows a decent fps, you should be set.

my knowledge of intel chipset setups is extremely limited (had a intel i810 I tried using for SDLMame in one of my comps, but swapped it out for a nvidia because of the grief in configuring it and the inabilty to get any speed out of it (it also using onboard RAM), while every nvidia I've used just seemed to work really well (really well as in milage varies with card model).

unfortunately with your chipset, your fps in WoW will be rather low, as in probably 5 - 8 fps and even lower in higher populated areas. after you do get it configured and running, you may decide you will want to get a faster/different GPU to increase that.

My setup is an older AMD Athlon 1800+ with an Nvidia 7600 GS and I get 35 - 50 fps in open areas and 15-20 in higher populated areas.

with your intel, yyou could try to use software rendering if all else fails and load the xerver-xgl package from the repositories. (this may help get you going, but no guarantee on fps, intrinsically slower due to CPU doing bulk of work.

post back on how it's going!!

---

### Post by Full-choke on 2008-01-20
Well, running the gears I was getting 1385-1388 FPS on average.  Is that pretty good?  Granted the CPU was at 30% range.  If I do a lot of CPU load (bump up to 50% or so it jumps up to 1500+, what's up with that?

Also, what is the xserver-xgl package?  What all is that going to do to significantly lower my FPS in game play even if it works?

Thanks,
F-C

---

### Post by gspat on 2008-01-20
server-xgl runs as emulation, so CPU does all the work.

---

### Post by Full-choke on 2008-01-20
Okay, now I'm not 100% sure on using repositories to get things?  How would I go about getting this package?

Also, is there a sure way to get it off so that if it doesn't work I can get back to the way things were and it won't bog my poor little CPU (P IV 3.2)

Thanks,
F-C

---

### Post by gspat on 2008-01-20
sudo apt-get install xserver-xgl

then I believe you type "xerver-xgl" to get it running...

if it doesn't work for you, just sudo apt-get remove xserver-xgl from the terminal and it's gone.

be sure to backup your xorg.conf file first just as a precaution.

if you get the gears and it runs.. try to run WoW and see what happens first, then try using xserver-xgl.

---

### Post by Full-choke on 2008-01-20
installed xserver-xgl and ran WoW...no go.  But, it doesn't run xserver-xgl by typing "xserver-xgl", any other ideas on how to run it?

F-C

---

### Post by gspat on 2008-01-20
before you try that.. what does WoW do? does it run the loader program (~/path-to-exe/loader.exe) and have you modified the wtf file to use opengl?

---

### Post by Full-choke on 2008-01-20
When I run WoW the CPU hammers on dang near full cap.  The screen will go black for a few seconds and then it clips back into the normal window and says "Wine unable to start 3D Acceleration."  Which is where I've been since yesterday afternoon.

F-C

---

### Post by Full-choke on 2008-01-20
BTW, I am starting through Terminal with 'wine "C:\Program Files\World of Warcraft\WoW.exe"'

F-C

---

### Post by gspat on 2008-01-20
ok... back to the beginning... let's check for your driver and go from there...

can you please post up your xorg.conf file?

---

### Post by Full-choke on 2008-01-20
Umm...I know I did it yesterday, but heck if I can remember how to get all the way down to xorg.conf...

How in the heck do I get all the way to it on terminal again?  Of course this will probably come to me tonight around 3 in the morning...

Thanks,
F-C

---

### Post by gspat on 2008-01-20
it's location is /etc/X11/xorg.conf

---

### Post by gspat on 2008-01-20
gotta go to work soon, so in case I don't reply quickly, here's some things for  you to try...

for your card and drivers... try this link... [http://ubuntuforums.org/showthread.php?t=412973](http://ubuntuforums.org/showthread.php?t=412973)

make sure you work your way through this page as well: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

hopefully, these will help you, I'll check back again ASAP to see how's going for you!

---

### Post by Full-choke on 2008-01-21
Okay...

So I looked at the first link.  Read through it, kind of made some sense.  I tried it, didn't work.  Now I need to restore my xorg.conf directory, but I can't remember how to get to it.  I know the command to copy it over once I'm to it, I just can't remember how to open up and view /etc...

Any help there would be tremendous.  As for the second link, that is what I was using for general info on the install.  I have completed everything on it, and I'm still not up and running.  Until I get my xorg.conf restored I'm stuck on my roommates Vista machine...the spawn of satan himself:mad:!

F-C

---

### Post by gspat on 2008-01-21
For the moment, just post your xorg.conf file here so I can see it...

it's at /etc/X11/xorg.conf

just right click it and click on open in text editor or something similar and copy and paste it.

---

