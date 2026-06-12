---
title: "Dell Studio 1535 with 965GM and X3100 VGA"
date: 2008-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by suncoolsu on 2008-11-10
Hi,
As you guys might recognize me now for all the posting for the past 1 month. Spamming and hunting for my resolution problems with any Linux OS (ubuntu in particular).

So I have a some good news for folks who are unable to use ubuntu with a resolution greater than 800x600 on this variety of dell. I have tried the distros in the following order -
1)Ubuntu (works with 800x600 with vesa only)
2)FC9 -- WSoD (no solution to get even 800x600 display)
3)OpenSUSE -- WSoD with OpenSUSE and 800x600 with SL 10.2 Enterprise Edition
4)Mandriva 2009 -- This is the bessst result so far...

So atlast - someone on the openSUSE forum informed me about Mandriva 2009 release. So inorder to have a linux distro on my 'poor' laptop which can give to a resolution greater than 800x600 - I downloaded Mandriva 2009 and isntalled. I didnt expect much from it though. And Mandriva didnt disappoint me as I met the familiar WSoD but since I have now been playing around with this WSoD problem a lot - so I tried to fix (as I always do) xorg.conf and changed the driver to "vesa" but I didnt change the 1280x800 display. and rebooted the system. 

TO MY PLEASANT SURPRISE.. I am now able to get a 1280x800 resolution on atleast this LINUX distro .. YAY YAY YAY (something is better than nothing)

Now to my surprise - I remember reading on this forum that its not easy to get a 1280x800 display with Vesa (or is it impossible to get a display more than 800x600 :confused: - seriously i am not sure.) Can anyone tell me whats the key here? And if some one can fix this problem I want to get back to ubuntu - because I like the ubuntu's HUMAN THEME a zillion times better than Mandriva's Oxygen Theme :(. But the silver lining is the 1280x800 theme.

Also when I try to reconfigure the drivers on this screen and test it with i810 driver(same as ubuntu's) - the test fails miserably - resulting in freezing of the screen - I have no clue - The knowledgeable people on this people pls comment.


Disclaimer - this post doesnt mean to degrade the "authority and quality" of Ubuntu (and its derivative) it is just for the sake of information of the poeple who have to satisfy themselves with 800x600 resolution on ubuntu (including me). It informs them that Mandriva is capable of providing 1280x800 resolution with Vesa driver. I am not claiming that Mandriva is superior or inferior to Ubuntu. Its my preference for 1280x800 resolution. 

Thanks a lot

Please someone solve this problem on ubuntu !! The human theme is awsome :D

B.

---

### Post by prshah on 2008-11-10
> **suncoolsu said:**
> 
with i810 driver(same as ubuntu's) 

The i810 driver is now deprecated; install the latest driver; Open a Terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install xserver-xorg-display-intel
```

This will replace the "i810" driver with "intel". That should clear up your problem.

Post back if you still have difficulties.

---

### Post by pwhitt on 2008-11-10
**prshah**:

i also have this laptop and am going to return it as soon as I get a shipping label.  as it arrived from dell (with 8.04 and the latest intel driver) it wouldn't even boot.  after many hours i was able to confirm with others that regardless which intel driver was used, this laptop will not run X without going into the infamous White Screen of Death (WSoD).

the best i or anyone else has gotten is 800x600 with the vesa driver.

i tried exactly what you suggest and i get the WSoD.  i tried a number of other fixes suggested in various forums - the only working method to get X running for me is to use vesa and it only supports 800x600.

---

### Post by pwhitt on 2008-11-10
**suncoolsu**:

i would guess there is a difference in the xorg.conf at least...  did your mandriva installation add a modeline for your screen?

i was able to get close to a stable 1280x800 resolution with modelines and vesa, but gave up.

can you post it?

---

### Post by suncoolsu on 2008-11-11
Shah Saheb,
Using the new intel drivers didnt work for me again :( .. I dont know what is the problem :( ...

Also I was playing around with mandriva resolution just to make sure I get it working with intel drivers - So this is what happened -- I dont know what did i do - the max resolution I can get now is 1024x780 (i guess) (but atleast its better than 800x600 :D ) 

I have been struggling to solve ubuntu issues with my hardware

Intel Core 2 Duo T8100 (64 bit)
Intel Mobile 965 Chipset
Intel X3100 VGA (358 Free Mem.)

Some strange reason anything doest seem to help and using intel drivers always results in WSoD...

** pwhitt:: ** do u still want the xorg.conf? I did a blunder which resulted in a resoltion lesser than 1280x800 .. lets hope i can figure out my blunder soon..

Thx
B.

---

### Post by pwhitt on 2008-11-11
> ** pwhitt:: ** do u still want the xorg.conf? I did a blunder which resulted in a resoltion lesser than 1280x800 .. lets hope i can figure out my blunder soon..

Thx
B.

i was just curious...  i've actually installed my old copy of WinXP on this POS.  i got an OK from customer service to return it...  i'm trying to see if there is hope of solving this before returning it but it isn't looking good.  i had the same problems as you and there seems to be no way around the WSoD.

i would guess it's related to the screen hardware and some modeline in xorg.

keep this in mind when shopping for hardware in the future - Dell really dropped the ball here and i never plan to give them another penny.

---

### Post by suncoolsu on 2008-11-11
pwhitt - just curious - Did u try Intrepid? May be that could work .. a lot of people who had same problems as mine managed to get intrepid on their systems, may be u ll be lucky this time?

Thx
B.

---

### Post by pwhitt on 2008-11-11
**suncoolsu**:
nope...  i've given up altogether until i see a solution posted by Dell, Intel or people in masses saying it works.  i'm still on the fence as to whether or not to return this thing.  i finally got the packing slip and have a week or so to return it.

i read most recently (in our other "Problem with Dell laptop..." thread) that a user was able to install intrepid and get an external screen working, but not the laptop screen.

it took enough effort to get this thing to run XP.  i'm not going to keep beating my head against the wall here - i'm just curious to see how it works out.  i'm in the middle of moving across the country and changing employers - not exactly an opportune time to tweak OS after OS.

just out of curiosity, can you post the output of:
`cat /etc/X11/xorg.conf |grep -i modeline`

i just want to see if there is a modeline for this screen in the conf file.  that might be an answer.

---

### Post by Dr_Snapid on 2008-11-12
My Studio 1535 ran no worries right from first boot using intrepid. Wireless wont work with WPA, and bluetooth wont pair my mouse, but everything else including graphics seems fine, right resolution and destop effects.
I'd love help with the wireless issues though.... another thread

---

### Post by Dr_Snapid on 2008-11-12
I should point out I only loaded it today and have not tested extensively. For example tested webcam, h/w buttons, hdmi etc etc.

---

### Post by pwhitt on 2008-11-12
> **Dr_Snapid said:**
> My Studio 1535 ran no worries right from first boot using intrepid...

just to clarify something - you have an intel chipset?  not the amd?

how long ago did you get yours?  as you indicate it booted right up with intrepid, since they aren't shipping with intrepid i have to assume you got the laptop with vista installed.  i believe they are more commonly configured with amd chipsets when sold with vista.

i also suspect there are differences between the screens in similarly configured laptops.  dell likely has several vendors for parts like hdds and lcds with approved components for these builds.

---

### Post by suncoolsu on 2008-11-12
I agree with pwhitt!! 
Thats why I think i belong to one of the people in the unfortunate league... my Dell Studio doesnt work with any of the Linux Systems. Fortunately the resolution was good in Mandriva!! and for the time being I am satisfied - if not happy. 

I would be really happy if ubuntu comes up with a solution soon !!

Guys who have Thinkpads have some hacks which worked for their system - unfortunately the Dell guys are lazy

Thx
B.

---

### Post by pwhitt on 2008-11-13
**suncoolsu**:

i don't know if you've followed this thread or not...

[http://ubuntuforums.org/showthread.php?t=892146](http://ubuntuforums.org/showthread.php?t=892146)

it seems there are a lot more people who ordered these preloaded with ubuntu that received malfunctioning paperweights.

---

### Post by suncoolsu on 2008-11-13
Yeah - infact I posted there as well - I have been on a lot of forums bugging everyone about my Dell Studio. All I wanted was to have a decent Linux Distro on my Laptop :( but I think this POS Studio doesnt seem to work with any linux distro - like - Slackware, FC9, openSUSE, Mandriva (now-atleast it runs at 1024x700s) 

I already encouraged that guy.. We need a lot more determined guys like him

Thx for the concern pwhitt

Hail u guyz

---

### Post by Prot on 2009-01-21
New patch out. 

Haven't tested it. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/297245](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/297245)

---

