---
title: "pages/windows too big"
date: 2009-05-27
forum: General Help
---

### Post by ejames82 on 2009-05-27
stuff on the screen is so big!  here's a screenshot.
i have been using hardy heron for about 3 months now.  i can honestly say that my "ubuntu installation expertise" leaves alot to be desired.  this is probably the reason why most web pages, and alot of the gui's and windows that come up are so big.  sometimes i am unable to get at the "apply" or "close" at the bottom of the window that is on the screen at the time (windows won't resize either).
maybe there is something i should be doing at installation, that i'm not, concerning screen resolution.  i have read numerous threads that explain the procedures for manually setting up the resolution, but the bits and pieces that i was able to make sense of, wasn't enough to "fit the puzzle together".
could this be a firefox issue?  
why is everything so big?
thanks for your time.

---

### Post by SOULRiDER on 2009-05-27
Youre using some really low resolution. Try reconfiguring your X server. Try this in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by steviefordi on 2009-05-27
In System > Preferences > Display (forgive me if that's not exactly correct, not on my Ubuntu machine at the mo), you should be able to change the screen resolution. If you cannot, you should at least be able to see what is is right now.

Assuming you cannot change the resolution to something smaller you're probably going to have to edit your /etc/X11/xorg.conf file. This can be tricky and you will need to get some info from your system. I'm not sure I can help but I'm sure this info will help people help you...

By pressing the button on your monitor that brings up the monitors menu, you should be able to see the refresh rate. A number followed by Hz or KHz. It should also state the current resolution.

Then open a terminal and enter:

```
sudo lspci -v > ~/businfo.txt
```

This should give a text file called businfo.txt in your home folder containing information about (among other things) your graphics card.

Post your refresh rate back here and attach businfo.txt and hopefully you'll get some help.

---

### Post by jerrrys on 2009-05-27
and if that doesn't work for you, there are two simple things to try...

1 press Ctrl and + or -. this will change screen size.

2 free up some real estate. this is how my CRT looks...

 [ATTACH]115319[/ATTACH]

---

### Post by ejames82 on 2009-05-27
thanks for the replies.
i will start by trying soulrider's suggestion.

---

### Post by ejames82 on 2009-05-27
soulrider,
i didn't receive an error message, or "no such directory".  i will need to do a little surfing to see how it works.  will let you know, thanks.

---

### Post by ejames82 on 2009-05-27
i also rebooted.
it has worked excellently!  what i am particularly pleased with, is that there is no scrollbar at the bottom.  everything fits on the screen.  thanks soulrider.

steve,
i will try to get that info, even though this worked.  i want to know this for my own peace of mind.  i've heard that knowing this about your graphics hardware saves you twenty times more work.  i've also heard that it's the "highest hurdle in the installation process".

jerry,
i have used that solution countless times.  every time i visited a new website, ctrl plus +.  i got to be pretty good at it.  it just takes the fun out of visiting new websites.

thanks for all the replies.  i will try to follow up on steve's advice, and post that info.

---

### Post by ejames82 on 2009-05-27
steve,
here is a screenshot.  i think this is what you refer to.
the path for me was:
system>preferences>screen resolution.

---

### Post by SOULRiDER on 2009-05-27
> **ejames82 said:**
> i also rebooted.
it has worked excellently!  what i am particularly pleased with, is that there is no scrollbar at the bottom.  everything fits on the screen.  thanks soulrider.

steve,
i will try to get that info, even though this worked.  i want to know this for my own peace of mind.  i've heard that knowing this about your graphics hardware saves you twenty times more work.  i've also heard that it's the "highest hurdle in the installation process".

jerry,
i have used that solution countless times.  every time i visited a new website, ctrl plus +.  i got to be pretty good at it.  it just takes the fun out of visiting new websites.

thanks for all the replies.  i will try to follow up on steve's advice, and post that info.

Forgot to mention you had to restart X, sorry. Im glad I was of help :)

---

### Post by ejames82 on 2009-05-27
i have a screenshot of the xorg.conf file.
it seems like more problems have surfaced, things that i do are slow to occur (the I-bar takes a while to appear), but i will take the good over the bad.  screen resolution, graphics, and display are very complicated and just trying to avoid the scrollbar on the bottom of the screen is nice.

i did find the monitor display frequency:

HF: 47.60KHz
VF: 59.92Hz
user mode

also as steve mentioned, the bus.info file has been provided in the home folder to access.  it's contents are too large to post here.  i will check out what's in there.  it'll take a while.

thanks to everybody for their help.

---

### Post by bmfc187 on 2009-05-27
hi i just wanted to chime in in say that i had had this problem and soulriders idea fixed it for me, too.  well, i did what he said and restarted and had the same problem, but then i went to system>hardware drivers and had to re-enable the proprietary nvidia driver, then when i restarted again it was the perfect resolution!  Thanks!!!no more BIG windows for me, either!!!

WWWWOOOOOOOOOOOOOT!!!!!!!!!!!!!!!!

---

### Post by steviefordi on 2009-05-28
It looks like SOULRiDER's superior experience got you a good solution for your X configuration. From the screen shot it looks like you can now change resolutions easily. You shouldn't need to worry about changing your Xorg.conf now. By all means do some research to better understand what it is and what it does, but I think yours is now fine.

Are you on a laptop by the way? If you are then maybe like mine there is only one decent resolution.

If you are having problems with the screen rendering slowly, it's probably that you need to enable a proprietry driver like bmfc187  (a few posts above) did.

Ubuntu won't enable these by default because they are released under a non-free (as in freedom) licence. The source code is not available (certainly not for the Nvidia ones) and that goes against what Ubuntu and Debian in general stand for. 

Unfortunately the 'free' drivers for Nvidia can be a bit unusable at the moment for certain cards - hence slow screen rendering. So you're better off enabling the proprietry ones. Hope this helps...

---

