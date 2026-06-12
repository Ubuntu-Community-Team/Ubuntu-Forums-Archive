---
title: "Gnome 3 looks weird"
date: 2011-08-18
forum: Desktop Environments
---

### Post by blonkler on 2011-08-18
Just installed Gnome 3 via UGR and the top and bottom of the screen wont render as it should, any ideas anyone?

[IMG]http://img580.imageshack.us/img580/5373/screenshotho.png[/IMG]

---

### Post by willgk on 2011-08-18
This is caused by ATI's drivers. Gnome 3 does not like them. Disable the Proprietary drivers and just use the open source ones. You won't have video acceleration but that's what we get right now sadly.

Now hopefully i didn't stick my foot in my mouth and you don't have an ATI card :P but here's to hoping ;-)

---

### Post by blonkler on 2011-08-18
Ok, thanks!
I have an ATI graphics card I'm afraid, so I just hope they'll have bettter support for ATI in the future.....

---

### Post by lkjoel on 2011-12-07
I've got the same problem, but unfortunately, my card is too new for the open source ones :(

---

### Post by cbowman57 on 2011-12-07
Have you tried adding **export CLUTTER_VBLANK=none** to your .profile?  It's been known to help with some vidcards.

You can try it from the terminal first to see if it does anything to cure the problem.

---

### Post by typhoon_tip on 2011-12-08
I'll try too, one thing I noticed is that Clutter is extremely laggy when moving windows around, possibly because of the VBLank issue and FGLRX driver.

---

### Post by typhoon_tip on 2011-12-08
Yep, totally fixes the laggines when moving windows around, but the driver problem remains there. Until they post the fix (December maybe and January should be sure).

---

### Post by cbowman57 on 2011-12-08
Yeah, I hate to beat a dead horse, & if you run Windows ATi makes some of the most powerful cards on the market, there just aren't good drivers to support it on Linux.

I'm glad that the suggestion helped in some small way for now.

Maybe Santa will bring all you ATi guys some great drivers.

---

### Post by typhoon_tip on 2011-12-08
> **cbowman57 said:**
> Yeah, I hate to beat a dead horse, & if you run Windows ATi makes some of the most powerful cards on the market, there just aren't good drivers to support it on Linux.

I'm glad that the suggestion helped in some small way for now.

Maybe Santa will bring all you ATi guys some great drivers.

Loll not that I like Gnome 3, I just hate that I cannot use it because of this :D So far I prefer Unity anyway.

If you set it properly (and not all cards unfortunately are the same) ATI works amazing also on Linux. I am able to use Torcs at nearly 100 fps on my ThinkPad T400 laptop.

---

### Post by cbowman57 on 2011-12-08
Yeah, I used to use ATi it just seems like it's so much hit & miss finding that good combination. Nvidia might not be the powerhouse it once was but they are pretty well supported across the board. Occasionally there is a bad combination but for the most part you can count on them out of the box.

Funny about personal preferences, when the change started coming to ubuntu I used Unity for quite a while, made it do what I want and looked decent doing it, then I tried gnome shell & I was hooked. :)

---

