---
title: "[SOLVED] Disable 60 second shut down timer?"
date: 2008-11-11
forum: Desktop Environments
---

### Post by Ed.Corcoran on 2008-11-11
Does anyone know how to disable the 60 second timer in the new shutdown menu? My tower is below my desk, so I accidentally bump into the power button all the time. I've already had the computer shut off twice accidentally since I upgraded to Ibex and its getting really annoying.

I like the new shutdown menu and all, but I just can't stand the 60 auto-shutdown timer.

---

### Post by Ed.Corcoran on 2008-11-11
Bump.

---

### Post by binbash on 2008-11-12
I am looking for a solution to this also.

---

### Post by Ed.Corcoran on 2008-11-13
Bumping again. Anyone have an idea?

---

### Post by binbash on 2008-11-14
Bump

---

### Post by Ed.Corcoran on 2008-11-15
Sigh. Bump.

---

### Post by skullmunky on 2008-11-17
Hi, I don't have a solution exactly because i'm not using Ibex yet - but I had a similar knees-bumping problem with an Antec case with overly sensitive power buttons: change the BIOS settings so you have to hold the power button down for a while before it does anything; and physically disconnect the reset button.

---

### Post by Ed.Corcoran on 2008-11-17
I bet you have the same Antec case I do. It's metal, with power buttons and USB ports right on the top.
I've physically disconnected the reset button already. That was a major problem. I was always accidentally hard rebooting my computer. The reset button went straight to the bios with no feedback from the OS. At least the power button triggers the OS rather than just going off.
Right now, I have it set in the BIOS that holding the power button turns the computer off hard, useful if the machine is totally frozen. I don't want to loose that, but it's not the end of the world. I can always flip the on/off power switch on the power supply.

Still, a fix to this new "feature" in Intrepid would be ideal.

---

### Post by Ed.Corcoran on 2008-11-17
Also, if anyone out there can point me to the config files for the shut down program, I can probably figure it out myself pretty quickly. But I just dont' have the time right now to go fishing around in /usr/ trying to find a config file of a program I dont' even know the exact name of.

---

### Post by Ed.Corcoran on 2008-11-22
Bumping again.

---

### Post by hictio on 2008-11-22
I believe we should start taking bets on this one :D ...
And perhaps on this one as well: [Location of Desktop settings for New User](http://ubuntuforums.org/showthread.php?t=975914)

---

### Post by skullmunky on 2008-11-22
> **Ed.Corcoran said:**
> I bet you have the same Antec case I do. It's metal, with power buttons and USB ports right on the top.

:) this one?
[http://www.antec.com/usa/productDetails.php?lan=us&id=81602](http://www.antec.com/usa/productDetails.php?lan=us&id=81602)

I like it other than that little annoyance.  Although it was a pain having to buy a special internal cable to connect the 1394 port on the front.  And in the end I don't know what's so great about being able to rotate that little top part 15 degrees....

---

### Post by Ed.Corcoran on 2008-11-22
Almost. Mine has an aluminum side panel rather than a clear one.
I wasted a bunch of time trying to get the 1394 port on the front to work with my motherboard until I realized that I never use 1394 anyway. :)

---

### Post by shcaesar on 2008-11-23
Got the same question

---

### Post by Ed.Corcoran on 2008-11-29
Bump.

---

### Post by jmacx81 on 2008-11-29
I'll bump that

---

### Post by Ed.Corcoran on 2008-12-05
Bumping again. Somebody has to know something. Anything.

---

### Post by Zorael on 2008-12-05
Well, you could disable the button, I guess. In *Power Management -> General tab -> When the power button is pressed*.

---

### Post by jmacx81 on 2008-12-05
I'll bump again, I think there has to be a better fix to that. I just haven't found anything yet either.

---

### Post by Ed.Corcoran on 2008-12-06
I tried that, but Power Management only gives me "Ask Me" as an option. I can't turn the button off in the BIOS either, so it's probably a poor design choice in my motherboard. I had to unplug the reset button from the motherboard because it became a problem (it hard reset when you touched it). I can't do that for the power button, because I need it to turn the computer on.

---

### Post by adult swim on 2008-12-07
hey guys, found your thread when searching for another one.  this solution came up using gconf-editor.  you can disable the power button from there with the nothing option and i guess shutdown with sudo shutdown -h now  from a terminal.
[http://ph.ubuntuforums.com/showthread.php?t=873892](http://ph.ubuntuforums.com/showthread.php?t=873892) post 3

---

### Post by Ed.Corcoran on 2008-12-07
Thanks! That fixes my problem in an even better way. I never intentionally try to shut down my PC by pressing the power button, so this is exactly the way I want it work. I can still shut down from the System menu, so I don't need to shut down from the terminal.

---

### Post by yeeshkull on 2009-10-16
Here's the proper way to disable the shutdown timer:

1) Right click on red "Power" button (top right hand corner of screen).

2) Select "Preferences".

3) Uncheck "Show confirm dialogs..." box (3rd one down).

4) Hit "Close" and you're done.

---

### Post by sports fan Matt on 2009-10-16
I don't see that in Karmic.

---

### Post by dani.savu on 2009-10-23
@yeeshkull: That worked in Jaunty, but not in Karmic

This command line does the trick in Karmic:

gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true

---

### Post by brookie on 2009-10-31
Sweet! That was driving me nuts in Karmic. I started gconf-editor in the terminal and went to /apps/indicator-sussion and clicked the box suppress_logout_restart_shutdown instead of running the command line above. There was a way in intrepid to start gconf-editor with a GUI from the menu, like Run or something? 
Thanks again, 
brook

---

### Post by Bayu on 2009-11-19
> **dani.savu said:**
> @yeeshkull: That worked in Jaunty, but not in Karmic

This command line does the trick in Karmic:

gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
That works perfectly, but **[COLOR=DarkRed]how can we change the timer?[/COLOR]** (e.g to 5 secs)

---

