---
title: "Another NWNightmare :) (3D)"
date: 2005-05-29
forum: Gaming &amp; Leisure
---

### Post by Zingam on 2005-05-29
Has anybody successfully played NWN on Ubuntu?

I have a notebook with 512Mb RAM, Mobility Radeon 9700/128Mb & P4 3.2GHz, Realtec AC'97 codec (I think 655). So I think this should be enough for NWN.
While still playing the tutorial at 1280x800 everything was perfect but after moving to Chapter One. The game became unplayable. There is constant HDD activity that stops the gameplay constantly. Its unplayable. The effect is if I play the game on a machine that does not have enough RAM. If I stay on a single spot and don't walk around the FPS are quite high but if I move a little bit - the constat swapping begins again.  When I quit: Ubuntu is fine.

BTW. I have installed 1.65.

Any ideas what could be the problem? Is it a video driver issue, ESD issue (ALSA does not work) or somethings wrong with the game?

Unfortunately I don't have any other Linux games to test. BTW there is some cracking noises even when the game is running smoothly. So I suppose my sound support is not the best.

---

### Post by Zingam on 2005-05-29
I installed ATI 8.12.10 but the game still runs crappy after the initial chapter and it also crashes now.

---

### Post by DarkKnight on 2005-05-29
[QUOTE=Zingam]Has anybody successfully played NWN on Ubuntu?

I have a notebook with 512Mb RAM, Mobility Radeon 9700/128Mb & P4 3.2GHz, Realtec AC'97 codec (I think 655). So I think this should be enough for NWN.
While still playing the tutorial at 1280x800 everything was perfect but after moving to Chapter One. The game became unplayable. There is constant HDD activity that stops the gameplay constantly. Its unplayable. The effect is if I play the game on a machine that does not have enough RAM. If I stay on a single spot and don't walk around the FPS are quite high but if I move a little bit - the constat swapping begins again.  When I quit: Ubuntu is fine.

BTW. I have installed 1.65.

Any ideas what could be the problem? Is it a video driver issue, ESD issue (ALSA does not work) or somethings wrong with the game?

Unfortunately I don't have any other Linux games to test. BTW there is some cracking noises even when the game is running smoothly. So I suppose my sound support is not the best.[/QUOTE]
 Well, you're having better luck then me. :) 

Every time I try and run nwn I get a shared lib error that just won't go away...

You may also want to dumb the graphics down a little bit, the drivers for ATI are no where near as good as windows, which sucks but meh. 

Did you install a new copy or did you copy over a windows install?

---

### Post by slimb on 2005-05-29
did you try killing all sound to see if it made any difference?

cutting the graphics back a touch isn't a bad idea either.

minor things that may make a noticeable difference.

---

### Post by Zingam on 2005-05-30
[QUOTE=slimb]did you try killing all sound to see if it made any difference?

cutting the graphics back a touch isn't a bad idea either.

minor things that may make a noticeable difference.[/QUOTE]
 It seems the problem is in the ATIs drivers. According to the NWN Linux forums it is related to AGP bug which leaks memory. Exactly what it looks like: too much disk swapping!

There are also proposed workarounds but the first does not work for me. Now I need to compile some .o file :). I hope it works.

Does somebody know how to easily install some C++ programming environment :) I want to do OpenGL stuff. 
Since I cannot connect to Internet with my Ubuntu (I'm using Wireless WPA connection) I have to download everything form Windows with flash-get (coz I can't use apt-get) and then I dpkg it. So far I was able to install and compile ATIs driver new kernel... :) etc. It doesn't feel like the coolest thing on Earth.


BTW...
I downloaded the resource files from Biowares web-site. I wanted to try a pure Linux expirience and not a copy-from-windows-and-fix-the-install one.
Windows is Windows, Linux is Linux I hate these Linux "fans" who try to convert Linux to Windows and then talk about how much w1n90z3 sux and how much Linux rlz!

---

### Post by DarkKnight on 2005-05-30
I had some problems with the ATI drivers as well, it's all fixed now and nwn runs fine... but I have a crap load of error's in the console thing (very techy name, I know).

I have a screenie if anyone has had a similar issue.

---

### Post by Zingam on 2005-05-31
What have you done, DarkKnight? Nothing seems to work for me. Not even the Septor's patch.

:) It seems I should forget about Linux gaming... OK. I give up!

---

### Post by nautilus on 2005-06-02
Hmm, I play NWN daily, on my Ubuntu+AMD64 box, with my girlfriend mostly, on her Ubuntu+AMD32 box.

That last issue simply looks like a poorly scripted NWN module.

As for the ATI issue, mine spontaneously crashes out as well, with 512MB of RAM, my mouse pointer is laggy in menus (it moves about 1/2 after the mouse), but all runs smoothly. (it's not even choppy)

As for the slowness (swapping, thrashing), it's probably due to using high-definition textures, which eats a boatload of memory.

Again, it's likely a leaky driver.  ATI blows goats for fun and profit.  I, too, miss my NVidia card...  *le sigh*...

It's a shame too, because ATI is famous for excellent hardware, but their Linux support is, frankly, insulting.

---

### Post by graigsmith on 2005-06-03
[QUOTE=nautilus]Hmm, I play NWN daily, on my Ubuntu+AMD64 box, with my girlfriend mostly, on her Ubuntu+AMD32 box.

That last issue simply looks like a poorly scripted NWN module.

As for the ATI issue, mine spontaneously crashes out as well, with 512MB of RAM, my mouse pointer is laggy in menus (it moves about 1/2 after the mouse), but all runs smoothly. (it's not even choppy)

As for the slowness (swapping, thrashing), it's probably due to using high-definition textures, which eats a boatload of memory.

Again, it's likely a leaky driver.  ATI blows goats for fun and profit.  I, too, miss my NVidia card...  *le sigh*...

It's a shame too, because ATI is famous for excellent hardware, but their Linux support is, frankly, insulting.[/QUOTE]
 i play neverwinter nights for hours at a time and never have any problems.  i was having problems with the 3d going blank, but that was a bios setting. (spreadspectrum was on)  

ati 9200 and im using the opensource drivers.  (the ones that only have support up to the ati 9200)  and i get pretty good performance.

---

### Post by DarkKnight on 2005-06-03
[QUOTE=Zingam]What have you done, DarkKnight? Nothing seems to work for me. Not even the Septor's patch.

:) It seems I should forget about Linux gaming... OK. I give up![/QUOTE]
 I had a copy installed on my windows partion, I copied it over, downloaded the Linux binaries, fixed the install, fixed my ATI drivers so they where being loaded, then just typed ./nwn.

So simple, yet it was a pain in the arse...

> Hmm, I play NWN daily, on my Ubuntu+AMD64 box, with my girlfriend mostly, on her Ubuntu+AMD32 box.

That last issue simply looks like a poorly scripted NWN module.

I only have the original Nwn with no mods...?
I'm on a 28.8K, so downloading mods isn't my thing. :)

---

### Post by wylfing on 2005-06-07
Aside from the fact that ATI's drivers might be causing you grief, I have never had luck copying NWN from a Windows install. I've used nVidia graphics cards forever, but I've gone through a lot of other hardware -- different mobos, sound, network, everything. In all cases I had problems with NWN whenever I copied it from a Windows install.

However, since you mentioned not having high speed net access, installing the Linux port from scratch might be impossible. (You have to download something like 200MB.) Maybe you can get someone to burn you a CD with all the Linux binaries and resources on it? Then follow the instructions at

[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

to the letter and you may have much better results.

---

### Post by meldroc on 2005-06-08
Speaking of NWN, has anyone successfully installed NWN from the Platinum package?  The fine developers set up installation scripts for Linux, as well as Linux binaries, but only for the Gold package.  How do you shoehorn those scripts so they work with the Platinum disks and install all the expansions?  I imagine once I have it installed, it should work - I have other games including Doom3 and UT2004 working fine on my system.

---

### Post by DarkKnight on 2005-06-08
It seems my problem was the update.

The modules I had were for 1.65 under windows, and the binaries where 1.29. 
Once I downloaded the update (took all night, lol) it works fine. :) 

> Speaking of NWN, has anyone successfully installed NWN from the Platinum package? The fine developers set up installation scripts for Linux, as well as Linux binaries, but only for the Gold package. How do you shoehorn those scripts so they work with the Platinum disks and install all the expansions? I imagine once I have it installed, it should work - I have other games including Doom3 and UT2004 working fine on my system.

IIRC, there are install instructions for the platnum edition on the nwn forums. :) 
[http://nwn.bioware.com](http://nwn.bioware.com)

---

### Post by tenshi-no-shi on 2007-03-02
Huh, seams strange. But hey I love my ATI Card, mainly because it's fully supported by the Open source Radeon Driver. I haven't played past the tutorial but well update when I do. Must be ATI's sucky drivers.

Oh and for the Platinum edition there is an install script on the forums for it.

---

