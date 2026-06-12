---
title: "Ubuntu optimization for games?"
date: 2005-05-06
forum: Gaming &amp; Leisure
---

### Post by DutchLau on 2005-05-06
Hello Ubuntu community,

Is there any way you can optimize Ubuntu to play games better? I know you can login with safe mode and do an xinit "gamefile" but is there any other way to get the best out of my hardware and so a little optimization?

Thanks,

DutchLau

---

### Post by cdhotfire on 2005-05-06
um, go to sessions, and take off the auto restarts to all the things, and then do like killall nautilus gnome-panel etc. and leave like X on. After open up terminal and the game is on. Or you can just install something like fluxbox, or xfce, and replace you slow gnome.:???:

Edit: wait i just saw your specs, and...
i think you should be able to run any game at full shizzel without problem. Dam thats a nice comp, can you give it to me.:razz:

---

### Post by DutchLau on 2005-05-06
It gets me from A to B  :razz:

---

### Post by Locomorto on 2005-05-06
[QUOTE=DutchLau]It gets me from A to B  :razz:[/QUOTE]
 Only problem is the poor GFX card, it does not do the rest of the system justice unfortuanly :(. Still i would not mind having it ;).

---

### Post by cdhotfire on 2005-05-06
[QUOTE=Locomorto]Only problem is the poor GFX card, it does not do the rest of the system justice unfortuanly :(. Still i would not mind having it ;).[/QUOTE]

Eh, 256 MB GeForce?

wth, that thing is powerful, it matches the system quite well.

How about $ 5. Okay okay, i was kidding.;-) $0.25? contact me.:-P

Edit: Also i think it takes you more than A to B, more like A to Z and back!:-?

---

### Post by penvzila on 2005-05-07
Yeah, but it's an FX 5200, which is a POS.  The 256 megs of RAM don't really mean much.

---

### Post by DutchLau on 2005-05-07
I was actually considering optimizing Ubuntu for my two other PC's which are far from the monster I'm sitting behind now (which I put together 4 days ago). 

This is one of the PC's:

AMD XP Thoroughbred 1700+ @ 2.0 Ghz with standard XP 3000+ fans, ASUS A7S333, 512 MB PC 266 DDR Ram, Dual 160 ATA HDD's (which are both 75 % full), 128 MB GeForce FX 5200 with Ubuntu i686.

This is the other:

Pentium 3 @ 1Ghz, 512 MB PC 133 Sdram, Dual 40 GB IDE HDD's, 32MB GeForce 2 GTS with Ubuntu i386.

So yeah, I was asking for optimization for the 2 other ones. The AMD machine is pretty good with Linux, and the Pentium is quite alright. Both run Americas Army perfectly, the Pentium 3 is also reasonable, but I was wondering if they could be better. Is there any *easy* way to install Fluxbox for Ubuntu that you can choose that it's Fluxbox at the startup or something, but still keep Ubuntu for gaming?

Thanks,

DutchLau

---

### Post by crane on 2005-05-07
[QUOTE=penvzila]Yeah, but it's an FX 5200, which is a POS.  The 256 megs of RAM don't really mean much.[/QUOTE]

I just installed a new card, my previous was a 5200. It played/worked quite well.
Very nice card, but that is not really the subject of this post is it?

I'm not real sure on how to optimize but you may want to check out [xorg's site](http://www.x.org) as well a [nvidia's site](http://www.nvidia.com)  you may find some helpful info there as well.

Good Luck!

---

### Post by DutchLau on 2005-05-07
[QUOTE=penvzila]Yeah, but it's an FX 5200, which is a POS.  The 256 megs of RAM don't really mean much.[/QUOTE]

HEY!!

Don't diss my video card!  :mad:  I spent good money on it! I get 4000 FPS with glxgears on a good day and I have a minimum of 120 FPS with America's Army on a good server!  :razz: 

The FX5200 is my pick though because it had lots of memory and that's what you need for video editing/graphic design (or both)  :) 

(Just to remind people about the subject of the post - how do I optimize performace for my two *other* PC's - NOT THE ONE IN THE SIG)

Cheers,

DutchLau

---

### Post by cdhotfire on 2005-05-07
[quote] Is there any *easy* way to install Fluxbox for Ubuntu that you can choose that it's Fluxbox at the startup or something, but still keep Ubuntu for gaming?[quote]

$ sudo apt-get install fluxbox fluxconf fbdesk fbpager bbmail wmfrog :), then choose fluxbox from sessions at startup.;-)

---

### Post by igloo on 2005-05-15
[QUOTE=DutchLau]The FX5200 is my pick though because it had lots of memory and that's what you need for video editing/graphic design (or both)  :) [/QUOTE]

Performance-wise, an FX5200 is roughly on par with a high-end GeForce 2, or a vanilla GeForce 4. Ask anyone (myself included) who "upgraded" from a GeForce 2.  

Don't get confused by model numbers: the only real judge of performance is relative cost. If you only pay £30 for a new-model video card, don't expect it to perform as well as the "older" model sat on the shelf next to it, going for £200.

The only thing it has over those other cards is hardware DX9 support, which is by-the-by because it isn't fast enough to do anything useful with those effects anyway.

Also, your understanding of what that 256 megs of video memory *does* seems to be slightly flawed.  Above the memory required by the frame buffer (w*h*bytes per pixel *# of buffers), the memory will only ever be used for caching texture maps. 

So, under typical use editing videos or playing with the GIMP, you're only ever going to use about 3.8 megs of it.

---

### Post by clarke.rainey on 2005-05-15
One thing taht I would suggest you do is get the K7 kernel instead of the i686 one... I have an AMD 64 running 32bit Ubuntu so I use the K7 kernel... and I think that your 1700+ is a K7 also...

I am not too sure how much of a difference that will make though...

---

### Post by rwabel on 2005-07-23
[QUOTE=DutchLau]HEY!!

Don't diss my video card!  :mad:  I spent good money on it! I get 4000 FPS with glxgears on a good day and I have a minimum of 120 FPS with America's Army on a good server!  :razz: 

The FX5200 is my pick though because it had lots of memory and that's what you need for video editing/graphic design (or both)  :) 

(Just to remind people about the subject of the post - how do I optimize performace for my two *other* PC's - NOT THE ONE IN THE SIG)

Cheers,

DutchLau[/QUOTE]
 see that's a funny thing! I've a Nvidia 6600GT and get barely 5000 FPS with glxgears. Damn what the heck is the problem with my nvidia drivers under linux?

---

### Post by Kemotaha on 2005-07-23
[QUOTE=rwabel]see that's a funny thing! I've a Nvidia 6600GT and get barely 5000 FPS with glxgears. Damn what the heck is the problem with my nvidia drivers under linux?[/QUOTE]
 Now I have to check my FPS when I get home to my computer to see how it compares.  The only difference with my system(see below) is the HDD and I have two 6600GTs.

---

### Post by mrf on 2005-07-23
[QUOTE=rwabel]see that's a funny thing! I've a Nvidia 6600GT and get barely 5000 FPS with glxgears. Damn what the heck is the problem with my nvidia drivers under linux?[/QUOTE]

glx gears isn't a good test of modern video card performance. It's like comparing mathematics degree holding applicants for a job by getting them to do basic math.

---

### Post by Kemotaha on 2005-07-23
[QUOTE=Kemotaha]Now I have to check my FPS when I get home to my computer to see how it compares.  The only difference with my system(see below) is the HDD and I have two 6600GTs.[/QUOTE]
 WOOOHOOO   I got 7000 FPS.  Sweet.

---

### Post by rwabel on 2005-07-23
[QUOTE=Kemotaha]WOOOHOOO   I got 7000 FPS.  Sweet.[/QUOTE]
 are you using the ubuntu nvidia drivers or the one from nvidia homepage? I don't think PCI-E makes that much a differences

---

### Post by charlieg on 2005-07-24
[list=1][*]Make sure you have hardware accelerated OpenGL.  This can be checked using 'glxinfo', and if you haven't, then there is decent documentation available for setting it up on Ubuntu.
[*]Check that X is running in 16 bit color depth mode.  It is often set to 24 bit by default, and this seems to be a somewhat unoptimized setting.  Setting it to 16 from 24 can easily double FramePS performance.
[*]Make sure you have ALSA set up right.  By default, Ubuntu uses ESD, and I found ESD to be slowing my system down.  This can be fixed to use ALSA + dmix:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)
[*]Make sure you're not running CPU hungry processes in the background.  Apps like Nicotine often consume unecessary CPU.  Things like GDesklets are also a classic CPU consumer.  You may also be running daemons that are consuming your CPU time but this is less likely.  For a machine as powerful as yours, your choice of DE shouldn't matter and running (eg) Fluxbox instead Gnome most probably won't help much.[/list]
That should get you started. ;-)

---

### Post by evilghost on 2005-07-24
[QUOTE=charlieg][list=1][*]Make sure you have hardware accelerated OpenGL.  This can be checked using 'glxinfo', and if you haven't, then there is decent documentation available for setting it up on Ubuntu.
[*]Check that X is running in 16 bit color depth mode.  It is often set to 24 bit by default, and this seems to be a somewhat unoptimized setting.  Setting it to 16 from 24 can easily double FramePS performance.
[*]Make sure you have ALSA set up right.  By default, Ubuntu uses ESD, and I found ESD to be slowing my system down.  This can be fixed to use ALSA + dmix:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)
[*]Make sure you're not running CPU hungry processes in the background.  Apps like Nicotine often consume unecessary CPU.  Things like GDesklets are also a classic CPU consumer.  You may also be running daemons that are consuming your CPU time but this is less likely.  For a machine as powerful as yours, your choice of DE shouldn't matter and running (eg) Fluxbox instead Gnome most probably won't help much.[/list]
That should get you started. ;-)[/QUOTE]

Note, I saw zero difference between the depth's of 16 and 24 in both glxgears, Doom3, and UT2004 so this may not be applicable to all configurations/systems.  Be sure to check :)

---

### Post by rwabel on 2005-07-24
[QUOTE=charlieg][list=1][*]Make sure you have hardware accelerated OpenGL.  This can be checked using 'glxinfo', and if you haven't, then there is decent documentation available for setting it up on Ubuntu.
[*]Check that X is running in 16 bit color depth mode.  It is often set to 24 bit by default, and this seems to be a somewhat unoptimized setting.  Setting it to 16 from 24 can easily double FramePS performance.
[*]Make sure you have ALSA set up right.  By default, Ubuntu uses ESD, and I found ESD to be slowing my system down.  This can be fixed to use ALSA + dmix:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)
[*]Make sure you're not running CPU hungry processes in the background.  Apps like Nicotine often consume unecessary CPU.  Things like GDesklets are also a classic CPU consumer.  You may also be running daemons that are consuming your CPU time but this is less likely.  For a machine as powerful as yours, your choice of DE shouldn't matter and running (eg) Fluxbox instead Gnome most probably won't help much.[/list]
That should get you started. ;-)[/QUOTE]
 damn the change to 16 bit was hell of a trick! thanks a lot:
rwabel@RALPH:/mnt/c $ glxgears
37229 frames in 5.0 seconds = 7445.800 FPS
44752 frames in 5.0 seconds = 8950.400 FPS
45500 frames in 5.0 seconds = 9100.000 FPS
45366 frames in 5.0 seconds = 9073.200 FPS
44766 frames in 5.0 seconds = 8953.200 FPS
45391 frames in 5.0 seconds = 9078.200 FPS
45482 frames in 5.0 seconds = 9096.400 FPS
44733 frames in 5.0 seconds = 8946.600 FPS

nothing more to say :-)
but fifa2005 still won't play nicely with cedega...damn EA!

Unfortunately 16 bit looks quit ugly :-(

---

### Post by charlieg on 2005-07-24
[QUOTE=rwabel]Unfortunately 16 bit looks quit ugly :-([/QUOTE]
 You can actually notice the difference between 16 bit and 24 bit color depths?  I know I can't.

Anyway, if it really bothers you, try 32 bit color depth.  The optimization of 16 bit seems to apply to 32 bit as well if I'm not mistaken.

---

### Post by rwabel on 2005-07-24
[QUOTE=charlieg]You can actually noticed the difference between 16 bit and 24 bit color depths?  I know I can't.

Anyway, if it really bothers you, try 32 bit color depth.  The optimization of 16 bit seems to apply to 32 bit as well if I'm not mistaken.[/QUOTE]
 well when I started fifa 2005 via cedega under 16bit the graphic was "bad", this wasn't under 24bit.

32 bit doesn't work for me. I've also read somewhere, that 32bit doesn't work with xorg. Did someone achieve 32bit with nvidia & xorg?

---

### Post by rejser on 2005-07-25
never tried fxgears... but wanted to see what I would get on my "old" computer..

XP 1800+
1024 mb ram
gf mx 440 128
120gb hdd + 80 gb hdd

started while burning a cd, then the numbers where 3700 - 4200.
Then I closed everything and got a this
25396 frames in 5.0 seconds = 5079.200 FPS
24438 frames in 5.0 seconds = 4887.600 FPS
24203 frames in 5.0 seconds = 4840.600 FPS
24607 frames in 5.0 seconds = 4921.400 FPS
25383 frames in 5.0 seconds = 5076.600 FPS
25251 frames in 5.0 seconds = 5050.200 FPS

Is that ok numbers?

---

### Post by Kemotaha on 2005-07-25
[QUOTE=rwabel]are you using the ubuntu nvidia drivers or the one from nvidia homepage? I don't think PCI-E makes that much a differences[/QUOTE]
 I am using the ubuntu NVIDIA drivers and running at 24 bit color

---

### Post by Bandit on 2005-07-26
[QUOTE=penvzila]Yeah, but it's an FX 5200, which is a POS.  The 256 megs of RAM don't really mean much.[/QUOTE]

I agree, I had a leadtek FX5200 and it was a POS. Performed the same as my ATI 7000VE. 
I couldnt put anything better then a FX5500 in my system. 
But the Gigabyte FX5500 256MB 128bit video card runs circles around the 5200 128MB 64bit I had..
Only about 20USD more also.. 
Only wished my shuttle XPC had a larger powersupply to run a 6200  :roll: 

Cheers,
Joey

---

### Post by rwabel on 2005-07-26
[QUOTE=Bandit]I agree, I had a leadtek FX5200 and it was a POS. Performed the same as my ATI 7000VE. 
I couldnt put anything better then a FX5500 in my system. 
But the Gigabyte FX5500 256MB 128bit video card runs circles around the 5200 128MB 64bit I had..
Only about 20USD more also.. 
Only wished my shuttle XPC had a larger powersupply to run a 6200  :roll: 

Cheers,
Joey[/QUOTE]
 about power supply, I've 350Watt. Is that enough or should I've more?

---

### Post by holomorph on 2005-07-27
I've run warcraft 3 on my old PIII 450 w/ 192 mb ram under openbox.  Just go to synaptic (or sudo apt-get install on the command line) and install the openbox package.  Then you log out, and select "openbox" under sessions and log back in.  your openbox session should give you a nice empty screen, right click (hmm, you may want the menu package installed too).

By the way, Openbox is, in my oppinion, a much handier window manager than metacity; I reccomend tryng it out in your for your regular gnom sessions ('openbox --replace &' in a command window).

---

