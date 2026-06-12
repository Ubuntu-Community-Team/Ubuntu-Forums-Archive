---
title: "Touchpad issues on Inspiron 1525"
date: 2008-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fallenstar on 2008-10-05
My touchpad is slow, and generally annoying me, as I like a really fast touchpad.

I used to run Suse 11.0, and to get the touchpad working, you had to disable the apparition of another mouse in the sax2 module. In my xorg.conf [Ubuntu] (sudo gedit /etc/X11/xorg.conf), it can see another mouse, while I don't have one. In Suse, you went through Yast/Sax2 to remove it. I can't find the equivalent in ubuntu.

There was also an option of Touchpad settings, which you adjust, and turn the speed up more. I installed "Touchpad" from Add/Remove Programs, but it won't initialise, giving the error message:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I added the line 
	Option		"SHMConfig"		"true"


but it still comes up with the same error message. I'm investigating the XF86Config at the mo.

Any ideas?

---

### Post by fallenstar on 2008-10-05
Ok, i forgot to restart. Touchpad works now lol

but that hasn't solved the sluggish problem, any ideas?

---

### Post by linusr on 2008-10-29
I can certainly confirm touchpad is still sluggish on Vostro 1500 running Intrepid.

Its worst than in 8.04 and forced me back to Vista.

does anybody has an solution to this?

---

### Post by Muflon on 2008-10-29
Hi 

What do you mean by 'slow'?

I have the same laptop running Hardy / Intrepid and after changing the touchpad speed in Preferences/Mouse everything is working at an acceptable pace.

Muflon

---

### Post by linusr on 2008-10-29
Hi Muflon,

Actually using touchpad is sluggish. I have chnaged mouse preference to be fast & sensitive enough, find it hard when i wanted to click or go through menu items.

using touchpad in vista is smooth enough but in Ubuntu I need use touchpad as my grandma. Move it to the button, steady & click it

not sure if nvidia drivers has anything to do with it

---

### Post by Muflon on 2008-10-30
> **linusr said:**
> not sure if nvidia drivers has anything to do with it

That might be the difference between your expirience and mine.  The movement of the mouspad is smooth in all applications for me but I have the Intel X3100.

Muflon

---

### Post by linusr on 2008-10-31
yes, confirmed. 

Disabled the proprietiry nvidia driver and touchpad works fine. Only problem no desktop effects.

---

### Post by bigmase521 on 2008-11-17
I have a 1525 running 8.10 w/ the Intel graphics and I have this touchpad issue too.  I tried setting the acceleration to its highest, and trying to adjust the sensitivity but I just can't get comfortable with it.  It's either too slow, or too jerky.. never smooth.  I like a fast trackpad too, very fast, but I also want it to be smooth. This isn't and it is getting annoying.

The other weird thing is, when the machine wakes up from suspend, the trackpad is very slow. When I go to the mouse preferences, it's set all the way towards "fast", but I have to click and drag it down to "slow, then back up to "fast".  Then it is back to normal speed.  I have to do this every time I come back from suspend.  Weird huh?  Thoughts?

---

### Post by Muflon on 2008-11-17
> **bigmase521 said:**
> The other weird thing is, when the machine wakes up from suspend, the trackpad is very slow. When I go to the mouse preferences, it's set all the way towards "fast", but I have to click and drag it down to "slow, then back up to "fast".  Then it is back to normal speed.  I have to do this every time I come back from suspend.  Weird huh?  Thoughts?

This is a known bug [https://bugs.launchpad.net/bugs/280148](https://bugs.launchpad.net/bugs/280148)

Muflon

---

### Post by freelook on 2008-11-17
I had this same problem at first.  I used the built-in acceleration support in the synaptics driver to solve it.  It has a parameter called AccelFactor that can be set.  So when you move your finger fast, the cursor will cover great distance, but small motions will be smooth and easy.

You'll have to fiddle around to get the settings that you prefer.  I could tell you what mine are but I'm not at my laptop.

The basic command would be: synclient AccelFactor=0.418

Or whatever.  There are a lot of other settings that can be tweaked as well, so I'd recommend a good look at the synclient manual (man synclient) if you're up to some tinkering.

I've noticed that some parameters for the synaptics driver work in /etc/X11/xorg.conf, while others don't.  If you can, I'd try putting the information in xorg.conf first, and if it doesn't work, put it in a synclient command and set the command to run at startup.

Why oh why didn't dell do a better job of configuring this from the start?

---

### Post by linusr on 2008-11-17
all of my touchpad nightmare got solved once i moved to 32-bit ubuntu 81.0.

previously was using amd 64 version

---

### Post by bobe84 on 2008-11-30
All of you using dell 1525 , try this and tell me if it worked for you 

[http://ubuntuforums.org/showpost.php?p=6282153&postcount=6]("http://ubuntuforums.org/showpost.php?p=6282153&postcount=6")

---

### Post by jsschreck on 2008-12-27
Yep, this certainly works a lot better than the native state of the touchpad. A little fast on the accel though as well as the cursor speed. I set them down a bit.

---

