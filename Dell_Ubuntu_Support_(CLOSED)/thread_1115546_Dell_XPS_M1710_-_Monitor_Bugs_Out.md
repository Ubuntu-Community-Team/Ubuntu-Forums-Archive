---
title: "Dell XPS M1710 - Monitor Bugs Out"
date: 2009-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mockdeep on 2009-04-03
I'm having a problem where the monitor on my laptop will spontaneously burst into an indecipherable mess of vertically and horizontally moving lines.  Image attached.  It always seems to happen when I'm browsing the web, but I am generally browsing the web when I am on my computer, so I'm not sure if that means anything.  This has happened as long as I can remember in Ubuntu, but it recently jumped significantly in frequency from once every week or two to four or five times a day.  When I close my monitor and open it back up the screen is back to normal.  It doesn't happen when I am in Windows.  How should I start trying to debug this?

---

### Post by mockdeep on 2009-04-05
Anybody? This is driving me nuts.

---

### Post by Pedro61 on 2009-04-05
I have exactly the same problem, on exactly the same DELL model - XPS M1710.

Its relatively infrequent for me (about once a week) but still annoying.  And also no problems with Windows. I only found out about the Closing the monitor "band aid" solution by accident otherwise I would still be rebooting.  My guess is that it might be a driver issue.

Any advice would be appreciated ???

Pedro

---

### Post by robbie d on 2009-04-07
I have an Inspiron 1720, similar occurance, except mine just offsets the lines so the screen looks like a brick wall.
what video card and drivers are you running????

---

### Post by mockdeep on 2009-04-08
It's an nvidia card running the accelerated graphics driver (version 180). GeForce Go 7900 GS.  I think it updated today from version 177, but the problem remains.

---

### Post by hcapy on 2009-04-08
The same problem, the same model of pc, dell xps m1710, i atacched my screenshots, i think this is because of the lights. Let me explain, when i installed ubuntu 8.04 at the first time i wanted to control my lights since the o.s., so i got a little aplication and installed it, some time latter the problem occoured. Then i decided to reinstall my ubuntu and not to install that aplication, so the problem never appeared. Now when ubuntu 8.10 was ready i decided to install the aplication and there were the problem again.



 Now i'm running on ubuntu 8.10 but i don't have the aplication of the lights installed so i don't have the problem, but is annoying to change the color of my lights since the bios.



 I hope we can find some solution or the new ubuntu 9.04 slve this problem.   



Hoo another thing, today was launched an actualization for the nvidia drivers, i wish this actualization solve the problm.





P.D. Sorry because of my bad english.

---

### Post by reiki on 2009-04-25
Try this:
putting this in the device section of Xorg.conf seems to fix the problem:

Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x1; PowerMizerDefaultAC=0x1"

the problem is with the powermizer when it changes the state. This edit to Xorg.conf forces the powermizer to be on high performance (and may run hot as a result) but appears to fix the screen problem.

please post here your results if this works for you or if it doesn't

You can also set PowerMizerDefault=0x2 for mid-level performance and you would then also change PowerMizerDefaultAC=0x2 (I think they have to match for this to work) and if you change those you may also have to change PowerMizerEnable=0x2 as well. I haven't messed with this so YMMV and I can not accept reponsibility if this screws anything up :)

I gleened this out of an nvnews post from February so I can't even take credit for it. Seems to work though.

---

### Post by mockdeep on 2009-04-25
Thanks.  I'm going to have to weigh the benefits of raising the power consumption versus living with the screen bug.  Oddly enough the bug has subsided back to once every few days, so I think I'll live with it for now.

---

### Post by reiki on 2009-04-26
I just picked up an M1710 from the place where I work for $450. It's a demo model. Never even had the battery installed in it. So I haven't had it long and haven't seen this bug yet. Does it seem to happen only when the machine is on for several hours?

We rarely use our laptops on battery. Almost always plugged in to AC. I'm debating on restoring it to original OS (XP Media Center) or installing Vista Ultimate on it and then shrinking teh windows partition down to practically nothing so we can dual boot Ubuntu 9.04. 

OR.... just forget about windows altogether and install Ubuntu as the only OS on the machine. 

If I did the dual boot thing, would the Media Direct button work? And if so... would I leave that Media Direct partition at the end of the DRIVE or just put it immediately after the windows partition?

I guess I'll have to play with it a while and see what we like and don't like.

---

### Post by mockdeep on 2009-04-26
I don't think it has anything to do with how long the computer has been on.  I have left it on for several days at a time without a problem.  I have noticed the bug happening on occasion at the moment I plug or unplug the laptop, which seems to agree with your findings.

I can't say anything regarding media direct, but my setup is dual boot, XP and 9.04.  I work almost exclusively from Ubuntu, mainly just booting into Windows to keep everything up to date, or to print, as I get buggy output printing in Ubuntu.  Haven't gotten around to looking into that yet.

---

### Post by FreeSoul on 2009-04-28
Wow, finally I see the same problem I've had for a while. I tried changing the nvidia drivers but nothing worked UNTIL...

ok, it's not really a fix, but it works.

**CTRL-ALT-F10 seems to reset the video driver.** Screen goes blank for a couple of seconds then comes back fine. 

Thanks for the tip reiki, but for now my fix is ok (don't play games) but will bookmark this thread...

FreeSoul

---

### Post by Andrew Hilton on 2009-04-28
[COLOR=blue][FONT=Verdana][SIZE=3]The other day I came back to my XPS and noticed a degradation in the graphics quality. Then there were artefacts on the screen ie lines and characters all multicoloured and twitching and flashing. Next time I switched it on, no image at all. Having exhausted my trouble shooting options, I came across these guys technomart in harrow, they suggested it was a graphics GPU fault and they could replace the chip. Took 3 days to fix and is working well. So far so good.[/SIZE][/FONT][/COLOR]

---

### Post by showgun22 on 2009-05-19
I am having the exact same type of problems 
Just seems that a lot of GPU graphic fault are happening
at the same time with the same model of Laptop with the same card
if that is the problem this seems to be caused by something

---

### Post by showgun22 on 2009-05-21
I have the same laptop XPS M1710 GeForce Go 7900 GS
The problem started with Jaunty downgraded back tried hardy as well as Intrepid and the problem still persist I started to believe the problem could have been the card/chip.
So formatted installed XP and all the good Dell software problem gone.


Dedided to dual boot with Jaunty even before installing the Nvidia drivers the problem started back again. The problem reside in an other place could be xrandr & xorg.
Found a link that listed adding the following to xorg

Section "Monitor"
    Identifier     "Configured Monitor"
    ModeLine       "1920x1200" 162.000 1920 1968 2000 2160 1200 1201 1204 1250 -hsync -vsync
EndSection

this has solve the problem I since have installed Nvidia drivers and it is running quite stable might have had one haps but reinsert the above and working fine.
Hope this will help some one else.

I was really desappointed to have to put back windows but looks like I will have to keep it untill the next upgrade "Karmic"
This in my opinion is a very serious problem when it comes down to video
workaround should have an official page
Good luck

---

