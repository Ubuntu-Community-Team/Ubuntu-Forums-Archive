---
title: "Amarok makes wierd graphics"
date: 2008-11-13
forum: Desktop Environments
---

### Post by oaxacamatt1 on 2008-11-13
Hi All,
I have recently installed Itrepid Ibex (8.10) on my Dell system that is several years old.  But I have come across a strange little quirk.  I installed Amarok and when I started it up I found that the prog had some odd behavior with it.  I found that some of the buttons on Amarok were transparent.  In other words I could see the Ibex brown background through the buttons.  ALSO, the prog started displaying brown bars on the bottom of the screen when I used the Amarok buttons.  

Now I know that I have not given that much info about my system but I should note that I hve installed 8.04 and 7.10 and maybe 7.04 on the same system with none of the aforementioned problems.  Which makes me think it is not necessarily a hardware problem.  

Any ideas,
Matt

---

### Post by ohzopants on 2008-11-13
I'll have to check if my Hardy install has the same issue.  I know I got an Amarok update a few days ago.

This may have something to do with KDE 3 vs 4.  Since you needed to install kdelibs (or is it kdebase?) to run Amarok you may have gotten the v3 libs and the v4 Amarok, or vice-versa.  You might want to check the package details through synaptic for compatibility.

---

### Post by oaxacamatt1 on 2008-11-13
Hi All,
Well this is strange...
I just started up the game Tetravex after opening the 'Add/Remove' Prog, not synaptic but the one on the drop down menu and this weird graphics came up again.

Check this out.
Matt

---

### Post by nikgare on 2008-11-14
Which garphic acrd are you using, which driver are you using, does the problem still happen after restarting X?

---

### Post by oaxacamatt1 on 2008-11-14
Hey Ohzopants, Nikgare,
I did a little investigation ala the first reply message.  I looked into the Synaptic Package Manager and searched for v3 and v4 libs and this is what I found.

v3 = libstdc++-v3, libnss3-1d

v4 = libv4l, libdb4.7, libdb4.6, libnss3-1d(again), libpt-1.10.10-plugins-v4l2, xserver-xorg-video-v4l

Not meaning to be flip, but so what? Can I delete/remove some of the v3 or v4 libs?  Another question is how can restart X?  Would you mind walking me thru it.  

I am using an ATI Radeon X800 card its appropriate driver which  installed nicely when I did a clean install on my system.
Cheers,
Matt

Nikgare, I like your avatar, are you trying to keep your head from blowing up?

---

### Post by nikgare on 2008-11-16
In Hardware Drivers, is there another version of the ATI driver available - try it .

Does the problem occur when you don't use compiz? ie turn off desktop effects?

---

### Post by Skripka on 2008-11-16
I noticed something along the same lines.......


When I boot my Kubuntu Ibex, I autoload Amarok on login.  For video playing I use VLC 0.9.x that is in the repos....Amarok is 1.4.x stable

Well,  If I just go and play ANY video in ANY media player (flv, mp4, DVD etc--played with VLC or mPlayer or Dragon Playe ) WITH Amarok minimized to tray-and no paused or any playlist loaded; I get WIERD checker graphic artifact dropouts on the video....hard to describe but imagine a video with only the black checkerboard spaces over it with video content on all the other spaces--is basically what it is, but the pattern of those checkers cycles through serveral patterns.

If I quit Amarok, checker artifacts go away.

Artifacts do NOT occur on flash videos streamed into a web browser.

It is bizzarro.

---

### Post by ohzopants on 2008-11-18
> **oaxacamatt1 said:**
> 
Not meaning to be flip, but so what? Can I delete/remove some of the v3 or v4 libs?  Another question is how can restart X?  Would you mind walking me thru it.


My original idea about KDE 3 vs 4 conflicts flew out the window when you had the same problem with tetravex which is a native gnome app.

You can restart X at any time by pressing CTRL + ALT + Backspace.
(This will kill X and log you out.  Save your stuff first!)

---

### Post by oaxacamatt1 on 2008-12-16
Hey Nikgare,
I finally had some time to look over my hardware/software for this odd screen issue, **see the first and third posts**.  I looked over one suggestion that asked me to turn off the compiz 'special effects', well there were not on to begin with, hmm.  So I went to the ATI/AMD website and downloaded the correct driver for my card.  BTW it is a ATI Radeon X800 (800SE) graphics card and fooled around with the for a couple of days.  I also looked up my card on Ubunu's site and found that it should be compatible.  Then I decided a totally different approach.  I went to Xubuntu and gave that a shot.  And what do you know the same things happen with Xubuntu.

I think it may be card or cardmotherboard issue.  But another odd thing is that with other versions of Ubuntu 8.04, 7 and 6 I never had this problem, hmm...

So now my question is How would you go about testing the graphics card?  Does linux have a super-special-fancy software for just this purpose?

Cheers,
Matt

---

### Post by oaxacamatt1 on 2008-12-16
Hey ohzopants,
I finally had some time to look over my hardware/software for this odd screen issue, **see the first and third posts**.  I looked over one suggestion that asked me to turn off the compiz 'special effects', well there were not on to begin with, hmm.  So I went to the ATI/AMD website and downloaded the correct driver for my card.  BTW it is a ATI Radeon X800 (800SE) graphics card and fooled around with the for a couple of days.  I also looked up my card on Ubunu's site and found that it should be compatible.  Then I decided a totally different approach.  I went to Xubuntu and gave that a shot.  And what do you know the same things happen with Xubuntu.

I think it may be card or cardmotherboard issue.  But another odd thing is that with other versions of Ubuntu 8.04, 7 and 6 I never had this problem, hmm...

So now my question is How would you go about testing the graphics card?  Does linux have a super-special-fancy software for just this purpose?

Cheers,
Matt

---

### Post by ohzopants on 2008-12-17
Linux has no such special utility (that I know of) but your motherboard might.  Does your motherboard have onboard video?  It it does, you may want to give that a try and see if you still get these problems.

---

### Post by oaxacamatt1 on 2008-12-19
Hi Skripa,
I noticed a while ago you posted on the Ubuntu forum about a video glitch that you experinced.  Did you ever figure it out?  I am experiencing a glitch that makes using Ubuntu and Xubuntu unusable.
MAtt

> **Skripka said:**
> I noticed something along the same lines.......


When I boot my Kubuntu Ibex, I autoload Amarok on login.  For video playing I use VLC 0.9.x that is in the repos....Amarok is 1.4.x stable

Well,  If I just go and play ANY video in ANY media player (flv, mp4, DVD etc--played with VLC or mPlayer or Dragon Playe ) WITH Amarok minimized to tray-and no paused or any playlist loaded; I get WIERD checker graphic artifact dropouts on the video....hard to describe but imagine a video with only the black checkerboard spaces over it with video content on all the other spaces--is basically what it is, but the pattern of those checkers cycles through serveral patterns.

If I quit Amarok, checker artifacts go away.

Artifacts do NOT occur on flash videos streamed into a web browser.

It is bizzarro.

---

### Post by Skripka on 2008-12-19
> **oaxacamatt1 said:**
> Hi Skripa,
I noticed a while ago you posted on the Ubuntu forum about a video glitch that you experinced.  Did you ever figure it out?  I am experiencing a glitch that makes using Ubuntu and Xubuntu unusable.
MAtt

Well, since that post I've upgraded to Amarok2.0 as well as KDE4.2Beta2, and that behavior is gone...When I upgraded both I forgot to test this to see if one might change something or the other would--so I don't know which did it.

---

