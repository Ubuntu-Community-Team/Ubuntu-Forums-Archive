---
title: "Dual Monitor issue in Jaunty"
date: 2009-05-04
forum: General Help
---

### Post by cullinane on 2009-05-04
Hey everyone, I know there have been multiple threads addressing setting up dual monitors in ubuntu, and I apologise if I'm retreading old ground at any point.
I have a Samsung Syncmaster 940 MW (max resolution 1440x900) hooked up via VGA to a Dell Inspiron 6400 running Jaunty.
I'm using a Radeon X1400 with the open source driver (am I right in saying that this card isn't getting a restricted driver?) I'm actually happy with the open source driver, its far better than Hardy or Intrepid- runs Compiz etc mostly fine.

In Windows I'm able to use the external monitor as a cloned screen or extend the screen. I'd be happy to do either on Jaunty (though preferably be able to switch it on and off as an extended screen)
Unfortunately, although Jaunty is able to recognise the monitor, it only gives me a few resolutions to choose from- the max being 1024x768. I read on another thread this is due to EDID information getting lost somewhere. Im unsure as how to resolve this though. I'm not confident enough to go editing important system files unless I'm sure it won't do damage! 
I hope someone has a suggestion. Thanks a lot guys.

---

### Post by Kareeser on 2009-05-04
Have you tried System -> Administration -> Display Preferences?

---

### Post by cullinane on 2009-05-04
Oh yeah I'm using the display preferences tool to configure it. It recognises the monitor no problem, the issue is the fact that its not recognising that the monitor can display 1440x900, or anything above 1024x768 for that matter.

---

### Post by stillious on 2009-05-04
I experience the exact same issue. I have a Dell D830 laptop (1280x800) with a Samsung LCD tv with a native res of 1440x900. With much messing around and logging off/on, the os finally realised that the tv was 1440x900.

*however*

The issue arises when you try to mirror the screen output, the options drop-down only shows 640x480, 800x600 or 1024x768.

Looks like we need help :)

---

### Post by cullinane on 2009-05-05
I'm posting the contents of my xorg.conf file below- 
Still fairly new to all this so not really able to make sense of it. From reading other threads it seems that you can input your preferred resolution for the external monitor somewhere in here. As I said above though I don't want to guess in case I break something!
Any help would be appreciated.

[COLOR="Red"]
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 812
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
[/COLOR]


Also, I ran xrandr and this also shows a very limited range of resolutions for the external monitor (VGA-0):
[COLOR="Red"]
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2304 x 812
VGA-0 connected (normal left inverted right x axis y axis)
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
[/COLOR]

---

### Post by cullinane on 2009-05-06
Hey Stillious, just to let you know that I managed to solve my issue myself!

After a bit of digging I found that it's possible to add your own video modes. This is how I did it:

I firstly had to create a 'modeline' which is all the monitor data associated with a particular resolution. To do this, I installed Powerstrip in Windows and got the modeline by following the simple guide linked to at the bottom of this page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Then I used xrandr to create a video mode using the new modeline for 1440x900. How I did this is detailed on the link above aswell.

Then with the new mode created, I had to associate it with my external monitor. I did this by typing xrandr --addmode VGA-0 1440x900 in the terminal. (Where VGA-0 is the monitor and 1440x900 is the name of the modeline)
Then the new resolution shows up in the display preferences settings in ubuntu.

I know your own issue is slightly different by I think this might be worth a try for you! (I can both mirror and extend the screen so this might help you too)

Let me know how it goes for you!

---

### Post by oliwek on 2009-05-26
thank you culliname for this link, really usefull  =D>

---

