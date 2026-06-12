---
title: "graphics not working (live-cd!)"
date: 2009-04-25
forum: General Help
---

### Post by slowmoe on 2009-04-25
Hey guys.
Yes, i have an ATI-card, but I searched for a long time before i decided to open a new thread, so please believe me when I say i tried to solve this with a lot of different solutions posted here...
And after all I think this is a major (though seldom) problem (read on to see how i come to this conclusion), but i can't file a bug-report, as I am unable to narrow down where it comes from exactly

I tried to upgrade to jaunty and everything worked out nice until reboot, but graphics were all messed up (i have a ATI AGP card with big-desktop running under proprietary drivers because opensource never worked out for me so far, so I am used to that error already ;)), so I went the usual way...

after 4 or 5 hours of trying nothing had changed I decided to download the live-cd and format my ubuntu to get a fresh install as i was sure this was because of a messed up setting i couldn't find because i'm kinda noob... but here it comes: (obviously i could have tried forever...)

[important part starts here]

Live-CD boots up nicely but but after splash, i hear the sound, (the drums, you now) obviously automatic login works.... but my screen is all black with the well-known red and blue scrappy lines above, only my mouse-pointer is up, visible without any error and perfectly responsive! tty works like a charm, going back to screen:0 (i guess - alt+f7) shows me the shiny new desktop background with blank panels on top and bottom but then ubuntu freezes

I don't get it, because the live-cd is supposed to use general working default drivers, and there should be no problem with gdm or X11...
So I got the log-files from the live-cd, but i can't see the error anywhere... everything i see is that the RADEON-driver is selected (shouldn't it be ATI?) and a warning that R600-chipset support is incomplete, and something about AIGLX failing and going back to software rendering...

I attach the whole var/log dir and I hope somebody is able to narrow down the actual error, as there should be no problem running a live-cd on my hardware, i guess :S
as soon as the error is found, I might post a bug-report, but so far that makes no sense to me.
If I can provide you with more information, please let me know!

Oh, and: I have a ATI HD2600 XT (AGP-version) running on a pretty old and slow but stable VIA K8T mainboard, with a Opteron 175 as chief of command, two monitors of different size and resolution (but default settings = clone were never a problem for this setup).


Thank you for your help - and I'm sorry for my bad english :)

[note: i don't think this is important, but were there new updates for intrepid on the same or next day to jaunty-release affecting gdm or X11?, because my backed-up intrepid still works nicely, but if I update it X11 is screwed up too, but at the moment I have not the time to play around so i don't know if this is a solvable problem]

---

### Post by slowmoe on 2009-04-26
ok, just a little update (despite the fact that maybe nobody cares) as I was searching for more log-files (e.g. gnome-desktop) I found the 'safe graphics'-mode on the live-cd... and it works...
I'm confused, because I thought the live-cd uses safe graphics by default :confused:

so I stick with intrepid and give jaunty another try maybe later and on a spare hd, when I have some spare time :) (I'm afraid it could cost me 'some' time to get the proprietary drivers up and running without a gui because configuring them was always trial and error and i still don't know whats the problem with the default driver of the live-cd)

btw: I still could use some hints where and how I can search for the actual problem AND does somebody remeber whats the difference between 'default' and 'safe graphics'?

thanks for the help everyone

---

### Post by Tipped OuT on 2009-04-26
Safe Graphics, I believe, disables compiz and/or uses a standard VGA driver.

---

### Post by slowmoe on 2009-04-26
I don't think compiz is an issue as I am talking about the live-cd :)

i just did a diff on some logfiles...

to be more precise on default-graphics and safe-graphics:
live-cd 'default' uses RADEON and 'safe-graphics' VESA

(this is not an easy task, because of all the time-stamps but:)
I also got a lot of differences between both versions of
- '.gnome2/accels/nautilus' (makes no sense to me)
- 'udev' of course, but most of it is just a different order of the devices or makes no sense to me (because I'm still not used to read hex-adresses :))
- 'Xorg.0.log' of course

interesting fact: the Xorg-log from the RADEON-setup states my 'RADEON HD2600XT AGP' as supported device! >(

the other files I could think of seem to be 'the same'.


_at the moment I see the RADEON driver shipped with jaunty as (at least) a difference-maker..._ and again:
this line is the only error i can find on all the logs:
**(EE) AIGLX error: Calling driver entry point failed(EE) AIGLX: reverting to software rendering**

and these warnings:
[B](WW) RADEON(0): R600 support is mostly incomplete and very experimental
[/B](are you kidding me?on a default driverthere should be no 'experimental' or 'incomplete' - this chip is not THAT seldom is he!?)[B]

(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x00ef00e0 is: 0x00ef00e0
(WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0x0000d000[/B]

I noticed earlier that my graphics device is a (seldom?) '**AVIVO**', maybe this makes a difference?

is there somebody out there that can make a use of this information or knows how to do that? (log-files anyone? ;))
AND
can somebody tell me if his RADEON HD2600XT AGP works with jaunty/the new radeon driver?

I think a non-working RADEON-driver is not a thing people should be forced to work-around or am I wrong and the only guy affected by this? Still don't believe it... 

Cheers

---

### Post by DwalerXIII on 2009-04-28
I have the same issues. My card is a radeon HD2600 pro agp.
After the splash (very pixelated) I get the black screen with red and blue on the top.

Running the cd in safe mode works but gives me the wrong resolution. Is this the radeon driver? If so there is no way I can get a working 9.04 install.

If the radeon driver is not used in safe mode, is there a chance I will get the right resolution after install?

---

### Post by slowmoe on 2009-04-28
'safe mode' runs VESA, and it would be nice if a ubuntu installed in 'safe mode', runs in 'safe mode', i mean with VESA, but I think after installation RADEON is going to be used, unless you force ubuntu not to use it...

I'm almost sure it is possible to run vesa-graphics after installation:
- I don't remember if jaunty-boot has a 'safe-mode'-option of itself? that would help :)
- maybe by changing a conf-file (which one I have no idea)
- and there is a boot-option that forces the live-cd to use the vesa-driver, maybe that works for the installation too, then you just need to add '**xforcevesa**' at the end of your ubuntu-entry in the grub-menu, but i'm not sure about that (would be the DIY-way of the first option)

once your installed ubuntu runs with the vesa driver, it should be possible and a easy taks to install the proprietary driver over the gui and when everything goes well, you're able to change resolution and have full 3d-support and so on after the reboot.
(you maybe have to undo the changes that were necessary to run the VESA-driver, if any)

I personally would head to this approach:
 i think it should be possible to install proprietary drivers directly after installation:
- there is a option on the live-cd to run ubuntu-installation with a optional driver-cd, that could work
- at least installation of the driver from command line should work, but I'm sure it's a bit tricky...

If you are in the mood to, feel free to try one of these and please tell us afterwards if something did actually help :)

i was going to test the last one, because it seems the straight solution, but I need this machine to be up and stable, so I won't take the risk for the next few days or weeks :)

[B]but as soon as I do and if I find a solution, I will tell you here

[/B]I wish somebody would care about the bug in the RADEON-driver... imho it is one. where do I post bugs in radeon?

Cheers

---

### Post by emarkay on 2009-04-28
Let's get all the Jaunty 9.04 ATI HD 2 series card data on one post to get this solved:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

