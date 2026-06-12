---
title: "Screen Resolutions"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by demonicdude on 2007-11-11
Hello,

Af of right now, the only screen resolutions available to me are:

1200x800       1152x768         800x600            640x480


Ok so, the 1200x800 one never works really, it just garbles up the screen when i select it. The monitor i'm using is actually a tv/monitor thing.. So i have the manual for it and it shows me what avaible resolutions i have and it lists all the way from 640x480 to 1280x1024 with 15 different ones in between. They also give me the horizontal frequency, vertical frequency, and dot clock frequency (whatever those mean >.>)

The 1200x800 one is not listed, which would explain why that would not work...

I want to figure out how i could get those listed supported resolutions available to be picked. I tried editing my xorg.conf file before and lone and behold, every time i tried i would either mess things up and have to figure out a way to replace the file. (thank you livecd >.>)

I also tried that sudo dpkg-reconfigure xserver-xorg, but i think i do something wrong because it also just messes up, leaving me with either a garbled screen, or no screen at all.

Can anyone help me figure out how to get these resolutions available :)?

---

### Post by Happy_Man on 2007-11-11
You say "dpkg-reconfigure xserver-xorg" does nothing? You use spacebar to select (I see that a lot when people say it doesn't help). 

What kind of tv/monitor thing are you using?

---

### Post by demonicdude on 2007-11-11
> **Happy_Man said:**
> You say "dpkg-reconfigure xserver-xorg" does nothing? You use spacebar to select (I see that a lot when people say it doesn't help). 

What kind of tv/monitor thing are you using?

It does something, except that something basically screws up the monitor >.>. 

Uhh the tv/monitor thing i'm using is an AKAI 20" LCD Television LCT2016


I will try doing dpkg reconfigure again.. Hopefully i dont screw up again XD. If i do screw up this is what i do to fix it...

I load up the livecd of Ubuntu Feisty and replace the livecd's xorg file with the one on the filesystem.

I have gusty btw. Upgraded from Feisty so..

Here goes..

Edit: So i did that, and i basically ended up with a black screen, So i reverted back to the old xorg.conf i had :P.

---

### Post by Happy_Man on 2007-11-11
What options do you pick when you go through the dpkg?

---

