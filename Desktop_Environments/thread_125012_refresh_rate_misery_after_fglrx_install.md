---
title: "refresh rate misery after fglrx install"
date: 2006-02-02
forum: Desktop Environments
---

### Post by andrewc2005 on 2006-02-02
Alright, after I finally got the fglrx drivers working I now have hardware acceleration, which is nice.  But even though everything seemed graphically more responsive, I started getting that little pit of nausea in my stomach, and my eyes felt like they weren't getting enough light, feelings I had long ago found were the signs of a bad refresh rate.  This is my first LCD monitor, thought that refresh rate didn't really matter but I guess it does.  Anyway, when I checked the screen resolution it was in fact at 60 mhz, when I remember it being 75 before.

So I've been messing around with it a while and I'm not sure why it was working before but isn't working now.  I changed the driver back to ati and it's still at 60.  At one point I accidentally started X from root and it was back to 75, but I can't replicate that on my own account. 

I tried online modeline creators but most of them asked for info I couldn't find in the monitor manual.  The two I did try gave me different values, and while I figure monitors today are more forgiving of wrong signals I didn't want to risk damaging a new monitor.

It's an Acer AL1913W LCD monitor whose maximum resolution (and the one I want it to run at) is 1440x900.

Cut and pasted from my monitor manual:
Input Signal: 
Simulated video frequency: 0.7 Vpp, 75&#8486;
SYNC Frequency: Horizontal 30kHz~82kHz x Vertical 56Hz ~76 Hz
Max Pixel Clock: 135MHz

Any ideas?

Man I have a headache.

---

