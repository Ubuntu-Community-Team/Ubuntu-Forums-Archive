---
title: "Scroll wheel disabled by toddler"
date: 2009-06-17
forum: General Help
---

### Post by naich on 2009-06-17
My youngest son (16 months) loves to bash away at the keyboard as he sits on my or my wife's lap.  So far the worst he has done has been to open up 85 Nautilus windows, until yesterday.  He was happily thrashing away when Jen noticed a message briefly pop up on the screen saying something about the mouse's scroll wheel.  She then found out that it didn't scroll any more.  Not only is it disabled for her, but it seems to be a system-wide setting because it's also disabled when I log in.

I've tried dpkg-reconfigure -phigh xserver-xorg but that doesn't fix it.  This is on Ubuntu Jaunty with a Logitech mouse.  Anyone know what key combination can turn mouse scroll wheels on and off?

Thanks.

---

### Post by jonobr on 2009-06-17
I feel your pain brother......

Is there any chance that the wheel has been broken?
Could you check it in another machine?

I say this as I have a closet full of broken things from kids,
including a mandolin, a trumpet, a ximeta 120gb hard drive, 3 razor phones...

A lot of these things malfunctioned due to baby spit, :-)

---

### Post by ManiacDan on 2009-06-17
Try to disable the accessibility options, it's possible one of the hidden options in there is "make the middle mouse button do something totally different."

I had a toddler once switch my brand new big screen TV over into the in-store-display mode, where it would just brag about its features over and over again.  took me weeks to figure out how to get it back (press all the buttons at once, like a good toddler).

-Dan

---

### Post by jonobr on 2009-06-17
Lol............

---

### Post by ddrichardson on 2009-06-17
> **naich said:**
> My youngest son (16 months) loves to bash away at the keyboard as he sits on my or my wife's lap.  So far the worst he has done has been to open up 85 Nautilus windows, until yesterday.  He was happily thrashing away when Jen noticed a message briefly pop up on the screen saying something about the mouse's scroll wheel.  She then found out that it didn't scroll any more.  Not only is it disabled for her, but it seems to be a system-wide setting because it's also disabled when I log in.

I've tried dpkg-reconfigure -phigh xserver-xorg but that doesn't fix it.  This is on Ubuntu Jaunty with a Logitech mouse.  Anyone know what key combination can turn mouse scroll wheels on and off?

Thanks.
Open a terminal and type xev. When it runs, click it and move the wheel - if text scrolls then it's registering an event and the wheel works, so you;d have ruled that out.

Count yourself lucky, a friend of mines toddler took a whizz on his laptop.

---

### Post by jonobr on 2009-06-17
Excellent tip, but the story of the toddler was better


 hilarious.....

---

### Post by ddrichardson on 2009-06-17
> **jonobr said:**
> Excellent tip, but the story of the toddler was better


 hilarious.....
That's easy for you to say, you weren't the one drying out a laptop.

---

### Post by naich on 2009-06-18
I feel a bit silly now because I've just tried a different mouse and it works with that one.  So it seems he's actually broken the mouse.  No idea what the message was about though.  It happened either during booting or POST, it seems.

So that's a camera and a mouse he's broken so far.  Most of his books are held together with tape too.

Anyway, big thanks to everyone for all the replies.

---

### Post by nothingspecial on 2009-06-18
> **ddrichardson said:**
> 

Count yourself lucky, a friend of mines toddler took a whizz on his laptop.

Mine puked all over ours.

---

### Post by jonobr on 2009-06-18
> 
Is there any chance that the wheel has been broken?
Could you check it in another machine?

I say this as I have a closet full of broken things from kids,
including a mandolin, a trumpet, a ximeta 120gb hard drive, 3 razor phones...

A lot of these things malfunctioned due to baby spit, 

JONOBR SHOOTS, HE SCORES...............

(although his eyes were closed at the time)

Glad to hear its working!

---

### Post by ddrichardson on 2009-06-18
> **nothingspecial said:**
> Mine puked all over ours.
Bet it didn't short everything like pee does ;-)

---

### Post by nothingspecial on 2009-06-18
> **ddrichardson said:**
> Bet it didn't short everything like pee does ;-)

Don`t know, I just chucked it.

---

### Post by jonobr on 2009-06-18
the problem with removing pee

is that it has athectic results which iss you off.
ractically s eaking though, rior  re ration and lanning revent against iss oor erformance,
as my mother used to say.

res ectfully

Jonobr

---

