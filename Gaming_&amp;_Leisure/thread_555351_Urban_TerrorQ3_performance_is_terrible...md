---
title: "Urban Terror/Q3 performance is terrible..?"
date: 2007-09-20
forum: Gaming &amp; Leisure
---

### Post by Phelan on 2007-09-20
Part of the reason I decided to dual boot ubuntu with XP is my aging laptop barely runs UT ([www.urbanterror.com](www.urbanterror.com)), which I am quite fond of playing.  Either way, it runs poorly in XP on my intel chipset video based HP DV1000, and I was told by another person in a game using an HP laptop (actually, an older less powerful one) that he ran Ubuntu and his framerate was about 80-100 solid at 800x600.  

I get anywhere from 30-60 with spikes where it drops down to 15-25 in XP.  I set it up and tweaked it exactly like it runs in XP, yet in 'nix I am getting 10-30fps.  What's the deal?

On the other hand, also, it runs it sort of like its in a window, there is black bars around the game screen, hence when I take the resolution up, the field of view for playing gets smaller and smaller.

Anyone help me improve fps a little, is there any tricks or something I am missing??  Is there anyway I dont have the newest intel drivers for my video because that made a substantial difference in XP.  Anyway to tweak the intel options like there is in XP?

If anyone could help I would love it, I am loving ubuntu in everyway except for this.  :confused:

---

### Post by Phelan on 2007-09-20
almost to 3rd page :(

*bump*

---

### Post by Phelan on 2007-09-20
How would I go about determing; A) what chipset my laptop has exactly, i've seen 855GM listed, 855GME listed, and 945...

b) how to determine if I need or can get a newer driver
c) if this will affect performance
d) how to actually update said driver if it exists.

---

### Post by Phelan on 2007-09-20
*bump* ..anyone? :???::neutral::confused::(:(:confused:

nobody uses q3 engine games with linux!!???

---

### Post by Mr. T on 2007-09-20
Calm down. :)

I read your postings several hours ago, but didn't reply because I didn't know if I could be any help. I think anyone who could have helped would have already, but like me didn't reply because your situation is fairly unique (obscure video chipset).

Since Urban Terror is my fav FPS in Linux, I'll post my suggestions, worthless as they may turn out to be:

(1) Go to Administration - System - Restricted Device Manager and if it shows anything to enable, click on the checkbox to enable it.

(2) Open a terminal and type in

sudo apt-get install chromium

I like using that game because it's a very quick and simple test to see if the 3D support in Linux is working properly or not. Run Chromium from the terminal (just type in chromium) and see whether it's playable or not, and if you get any problems with the graphics.

(3) I'm fairly certain there's a way to view devices in Ubuntu, kinda like the device manager in Windows. Google if you need to, or just check the stuff under Administration - System to see what you can do.

I hear Intel chipsets are open sourced and work fairly well, but there's always the possibility yours is not as well supported in Linux as it is in Windows. Best of luck though. :)

---

### Post by tolstoyboy on 2007-09-20
use this to detect your graphic setup and then to install the proper drivers for nvidia or ati. As far as i know many people suggest it and it works quite well...and it is basically automatic install....
Works great for me...although everyone is setup up differently...

"Envy"
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Urban Terror runs smoothly for me....amd64x2 with ati xpress 1100 using the latest ati driver(8.40), the one in the ubuntu restricted manager, or the install from Envy; which is just the ati 8.40 fglrx. I get 45 fps avg...and this is with the poor drivers...i can't wait for 8.42 next month...

---

### Post by rybu on 2007-09-21
Unless the map is extremely busy I get 90+ fps in openArena, tremulous and WoP at 1920x1200 on my laptop using 50% of processor cycles.   Some of these apps, like openArena come in an SMP compilation but I have no idea what that means as system monitor tells me it's only using 1 processor.  :confused:

---

### Post by asipi on 2007-09-21
intel does not provide a useable 3D accelerated driver to linuxusers...
so you won't be able to play man, that's why I only buy nvidia related video hardware stuffs. nvidia has the best and painless drivers for the linux users.

Anyway I am an Enemy Territory player but rarely I play urban terror also, ET has about 50-60 fps but UT always has 90 above fps with my not-so-fresh nvidia GF 6200 card.

---

### Post by Phelan on 2007-09-21
I will try what you guys posted and post back.  I know the intel chipset sucks, but I got the laptop as a present so I really can't complain.  I am currently doing federal air marshal training, I have a desktop sufficient enough to play pretty much anything, I just havn't brought it along.

will reply back :)

---

### Post by Phelan on 2007-09-21
Ok...n o restricted drivers, chromium runs great, and envy is for ati/nvidia, if I had ati or nvidia the game would play fine, but i have onboard intel which sucks.   I'ved tweaked UT to make it look like utter crap, and I can barely maintain 30fps...

Also, it's not full screen, what's up with that?

---

### Post by Mr. T on 2007-09-21
You can flick between windowed and fullscreen anytime in the game by pressing Alt+Enter.

---

### Post by Phelan on 2007-09-21
It's not a window.  it is showing a 640x480 or 800x600 screen inside of my laptops 1280x768 resolution.  If I put it to 1280x768, it's full screen...just 1-3fps.  There are black bars around the actual screen you can see, it's not being ran in a window.  It reminds me of the old doom 1 where you could hit + and - and the screen would get bigger and smaller.

---

### Post by Mr. T on 2007-09-21
Sounds like your laptop is not scaling smaller resolutions up to the size of your screen. Do the lower resolutions scale properly in XP? If they do, looks like the Intel drivers in Linux need some work.

---

### Post by Phelan on 2007-09-22
Yes XP does it fine.  I tried out the config I setup for linux and XP does about 50fps solid, occasional spikes to 90-100 and occasional drops to 30.

Anyway to check and see if I can get newer or better drivers for my chipset?

---

