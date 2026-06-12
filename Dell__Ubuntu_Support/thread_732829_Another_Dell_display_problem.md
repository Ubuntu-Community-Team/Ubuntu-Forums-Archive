---
title: "Another Dell display problem"
date: 2008-03-23
forum: Dell  Ubuntu Support
---

### Post by emmalg on 2008-03-23
I am sorry for starting yet another thread on Dell display problems but I haven't been able to resolve mine from the advice I have found.

I'm new to Ubuntu (7.10), although use Suns & Fedora at work (so am quite happy with the command line even if the commands are new) but have never had to set anything like this up before.

I have a Dell Latitude C600/C500 with ATI 128 Rage Mobility, as far as I have been able to discover the max resolution of the ~14" screen is 1024x768, so it is not one of the high res ones.  If I try to set the correct settings using the "Screens and Graphics" (ati drivers and Dell laptop display of the correct resolution) I end up with horrible issues!  The display is okay on the left hand side, then is repeated in vertical strips all over the left hand side (it makes me think of sampling problems).  I would have supplied a screenshot but I switched the laptop off before I got even more annoyed with it and myself!

I followed the advice I found on this forum, backed-up my xorg.conf file and ran the hardware settings setup (dpkg-reconfigure xserver-xorg), making sure that I specify the horizontal sync and vertical refresh (I took the numbers from the Settings and Graphics gui).

Unfortunately there still seems to be something wrong as Ubuntu insists on starting in a low graphics mode and the screen is tiny!  

Any advice would be appreciated, and the simpler the better as my brain is already melting!

Also if I need to do or check anything else for this specific installation some pointers would be great! :)

---

