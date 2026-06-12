---
title: "Drivers! 10.04. Sound / Graphics"
date: 2010-07-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamohammed on 2010-07-19
I have a Dell Studio 15 series (1535) lappy running Ubuntu 10.04...

Works pretty well. But my problem is that I dont have sound! Also, there is a graphics driver installed but its a limited driver (running 3d apps like games etc is painful!)...

Yes my sound card works... I had ubuntu 9.10 previously and sound works as well as the graphics.

Need help with these:
1. How to reset sound drivers and settings to default (was playing around with stuff in a fail attempt to get it to work)

2. Anyone got their sound to work? Whats your secrete...?

3. Anyone have ideas of what graphics drivers to use for 10.04? I tried the linux proprietary drivers from ATi site and cause my lappy to not boot :(

4. Anyone played Silent Hill: Shattered Memories for the Wii yet? is it worth a buy?

---

### Post by ajgreeny on 2010-07-19
For sound problems run alsamixer in terminal and make sure nothing is muted or set too low.  That often solves the problem.

For the graphics, what video card is it using?  If you don't know, run lspci in terminal and it will tell you on one of the lines of the output.

---

### Post by kamohammed on 2010-07-19
yeah, the sound isnt muted... in the sound settings there isnt any hardware or much options to select.

and graphics...its the embedded ATi Radeon HD 3450 that comes with the Dell Studio 1535... (3400 Series)... When I return home I will run the lspci and give you a better detailed read out...

---

### Post by ajgreeny on 2010-07-19
Have you actually run alsamixer?  It sounds from your comments as if you are just using the volume icon, or pulseaudio-volume-control, neither of which offer the options of alsamixer.

---

### Post by kamohammed on 2010-07-25
> **ajgreeny said:**
> For sound problems run alsamixer in terminal and make sure nothing is muted or set too low.  That often solves the problem.

For the graphics, what video card is it using?  If you don't know, run lspci in terminal and it will tell you on one of the lines of the output.

ran the lspci...

here is the related information:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

gonna try the alsa mixer now
-------------
apt-get install alsamixer .... failed :(

plus i did 
aplay -l
aplay: device_list:223: no soundcards found...
..........................................................

---

### Post by kamohammed on 2010-07-25
[http://www.alsa-project.org/main/index.php/Matrix:Main#Vendors](http://www.alsa-project.org/main/index.php/Matrix:Main#Vendors)
dont have my card...

Im kinda out of ideas atm... and exhausted from work... 

anyone have a direction to point at?
PS: im not worried bout the graphics. I am getting through with that. Just the sound issue kinda failing me ...

---

### Post by texaswriter on 2010-07-26
aptitude search alsa|grep mixer //<<--- one way of searching for alsamixer
apt-cache search alsa|grep mixer //<<-- another way of searching for alsamixer
User only one of the above unless one fails. 

One my computer it is gnome-alsamixer

sudo aptitude install <insert name of alsa mixer here>

sudo aptitude install gnome-alsamixer

---

### Post by kamohammed on 2010-07-26
Ok. thanks. I will try this when I return home... (gonna get fed up saying that...)

will let you know of the results...

---

### Post by kamohammed on 2010-08-17
ok... i have no idea what the hell happened... but i booted my system and ... there was sound... 
...
...
..
...

i think the last thing I did was used Synaptic Package Manager...
removed all alsa or anything with sound... then re-installed them...

(I did that a few weeks ago and I now booted the lappy since...)

Maybe this can work for other users with similar problems. Can someone justify this?

---

### Post by blob dob 11 on 2010-08-17
For some reason the solution to a lot of problems is turning it off and on again. :P

---

### Post by texaswriter on 2010-08-18
Glad that worked out for you!!! Could you mark the thread as "solved" ):P

---

### Post by texaswriter on 2010-08-18
Glad that worked out for you!!! Could you mark the thread as "solved" ):P

---

