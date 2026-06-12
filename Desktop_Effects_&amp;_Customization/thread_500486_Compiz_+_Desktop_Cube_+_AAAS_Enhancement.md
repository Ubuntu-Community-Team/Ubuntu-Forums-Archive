---
title: "Compiz + Desktop Cube + AA/AS Enhancement"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by WowMike2002 on 2007-07-13
Alright, currently I had my good friend help getting this installed and running, we had some Nvidia driver issues last night, and after work today I hopped on and figured it all out (Wasnt keeping my xorg.conf default properly.. all fixed now.. runs great!

My only problem right now is that when I am using the Desktop Cube and spinning it around, I notice the edges of teh cube are quite jagged, and was hoping by me forcing 16xQ AA, and 16xAS with Texture Sharpening.. that it might help it out a bit...  my current system specs are as follows:

CPU: AMD x2 6000+ (3.0GHz)
GPU: XFX XXX 8800GTS (320mb)
RAM: 4 gigs Mushkin 3-3-3-8 PC6400
Monitor: Samsung 226BW 22" @ 1680x1050/60

No lag whatsoever, and runs beautifully.. but here is a screenshot of me attempting to straighten these edges out into a nice crisp cube..  but, to no avail :-(  As you can tell if looking carefully, I have forced my card to the proper settings, and tweaked as muh as I could.. but still no luck.


Any issues with this? As it doesnt change even if I back down to basic settings for the card, or may it be a driver issue perhaps?

Any help would be appreciated.. thanks!

---

### Post by bdtgp on 2007-07-14
It's not like in games and such where you can adjust the graphics of everything.  Im pretty sure you would just have to live with those jagged edges until they implement something to get rid of them.  I think there is only one level of sharpness that it can figure out.

On the other hand, I could be completely wrong but I'm pretty sure thats what it is.

---

### Post by WowMike2002 on 2007-07-14
> **bdtgp said:**
> It's not like in games and such where you can adjust the graphics of everything.  Im pretty sure you would just have to live with those jagged edges until they implement something to get rid of them.  I think there is only one level of sharpness that it can figure out.

On the other hand, I could be completely wrong but I'm pretty sure thats what it is.

Yeah.. I'm used to being able to tweak it, and then everything thats loaded whether desktop or not is hit with it.. but if thats what it is, then thats what it is =)   Considering what the program is doing though.. you would almost think it could be readily tweaked :-)

---

### Post by bdtgp on 2007-07-14
I definitely agree.  Look around, maybe you can do it somehow; there are some geniuses on these forums.

---

### Post by panurge77 on 2007-07-14
Did you try [http://forums.opencompositing.org/](http://forums.opencompositing.org/) ?
I remember a thread about this subject on the old quinn-compiz forums, but can't find it now.

---

### Post by psyopper on 2007-07-15
WowMike - 

[Take a look at this thread]("http://ubuntuforums.org/showthread.php?t=273858&page=3"), you might be surprised at the results you are alredy getting...

;)

---

### Post by GlennW on 2007-07-17
> **WowMike2002 said:**
> Alright, currently I had my good friend help getting this installed and running, we had some Nvidia driver issues last night, and after work today I hopped on and figured it all out (Wasnt keeping my xorg.conf default properly.. all fixed now.. runs great!

My only problem right now is that when I am using the Desktop Cube and spinning it around, I notice the edges of teh cube are quite jagged, and was hoping by me forcing 16xQ AA, and 16xAS with Texture Sharpening.. that it might help it out a bit...  my current system specs are as follows:

CPU: AMD x2 6000+ (3.0GHz)
GPU: XFX XXX 8800GTS (320mb)
RAM: 4 gigs Mushkin 3-3-3-8 PC6400
Monitor: Samsung 226BW 22" @ 1680x1050/60

No lag whatsoever, and runs beautifully.. but here is a screenshot of me attempting to straighten these edges out into a nice crisp cube..  but, to no avail :-(  As you can tell if looking carefully, I have forced my card to the proper settings, and tweaked as muh as I could.. but still no luck.


Any issues with this? As it doesnt change even if I back down to basic settings for the card, or may it be a driver issue perhaps?

Any help would be appreciated.. thanks!

Sorry I can't help you with the settings as I'm quite the newb but I'd be very interested in your settings in how you ended up with your cube looking the way it does!! Everything for me works great except that my cube doesn't receed/shrink and tilt slightly (like yours). It just spins and maintains its full screen size. Every video I've seen has the cube spinning and dancing, unfolding, and whatever, smaller than full screen size and thereby showing off the background.

Any info would be appreciated.

Thanks.

---

### Post by psyopper on 2007-07-18
It's in the Compiz Config Settings Manager, Rotate Cube plugin. 

Enable the plugin, and in Actions tab look at the first listing, "Initiate" to see what keystroke(s) you need to initiate the tilt-a-whirl. I usually set the "Key" to "Button2." In X, Button2 is the center button/ click button on the scroll wheel.

To get the reflection take a look at the Cube Reflection plugin. To make the cube transparent there's a section in the Desktop Cube plugin for Transparent Cube.

---

### Post by GlennW on 2007-07-18
That did it! Thanks a bunch.... Nothing like some serious eye candy (that works well) when you're showing your skeptical friends why they need to convert.

---

### Post by SkiesOfAzel on 2007-07-18
It's simple really, just open nvidia-settings set your preferred AA and aniso settings and restart compiz. Your desktop WILL get alot slower though.

---

