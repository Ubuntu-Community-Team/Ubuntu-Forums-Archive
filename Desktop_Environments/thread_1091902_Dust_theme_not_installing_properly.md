---
title: "Dust theme not installing properly"
date: 2009-03-09
forum: Desktop Environments
---

### Post by Happy-Dude on 2009-03-09
Heya guys!!

(I've previously made a post here: [http://ubuntuforums.org/showpost.php?p=6868142&postcount=92](http://ubuntuforums.org/showpost.php?p=6868142&postcount=92) , but perhaps it is more fitting for me to ask in the Desktop Environments support thread.)

Basically, I love the Dust theme, but I can't seem to get the top and bottom panels (or the menus) to look like Dust's previews (black); instead, they are sort of white.

I didn't think this was a problem (since I switched to 0.3 version) until I noticed that 0.3 versions were still installing with the general black scheme. I noticed that Dust on my school Ubuntu machines looks like it supposed to, but the machine back at home doesn't have the black menus or panels.

Here is a quote from the post I made on the other thread:
> **Happy-Dude said:**
> Heya guys!!

So this is my first post on the Ubuntu forums, and I've been using Ubuntu in my CompSci class and recently installed it on a Compaq Deskpro EN (I'm thinking of going to Xubuntu 9.04 due to XFCE 4.6 and RAM issues).

I love the Dust theme ([https://wiki.ubuntu.com/Artwork/Incoming/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme) ), and I recall when I first installed it, the panel and menus were all black... Just to my liking :D .

Unfortunately, I seem to have run into a dilemma now: for the recent 0.3 versions, I can't seem to be able to get back the darker colored panels and such.

Here is what I mean:
[http://imgur.com/541W5.png](http://imgur.com/541W5.png)
Here you can see my Appearance settings for the Dust theme and the Clearlooks/ Murrine engine versions.

[http://imgur.com/542NX.png](http://imgur.com/542NX.png)
Here is my desktop screenshot, which would look so much better with some darker elements with the *correctly* installed Dust.

And would anyone know why DarkRoom displays just fine?
[http://imgur.com/543FP.png](http://imgur.com/543FP.png)
(old picture)

I believe the correct installation of Dust looks like:


Can anyone give me a little help here? I really appreciate it :) !!

Can anyone lend me a hand :) ?

---

### Post by Chemical Imbalance on 2009-03-09
Try this:

```
sudo apt-get install community-themes
```
This will give you the Dust theme from the repos (ensuring that it works)
Look in Appearances after you install it.
I suggest you first delete the Dust theme you just downloaded if you do this though.


Your problem might be that you don't have the correct gtk-engine installed for this theme you downloaded.  Check where you downloaded it from and make sure you make note of what engine it requires.  It could be something else though.

---

### Post by Happy-Dude on 2009-03-09
> **Chemical Imbalance said:**
> Try this:

```
sudo apt-get install community-themes
```
This will give you the Dust theme from the repos (ensuring that it works)
Look in Appearances after you install it.
I suggest you first delete the Dust theme you just downloaded if you do this though.


Your problem might be that you don't have the correct gtk-engine installed for this theme you downloaded.  Check where you downloaded it from and make sure you make note of what engine it requires.  It could be something else though.

Doing this now... Will edit once its done and report back on what I find.

---

### Post by Happy-Dude on 2009-03-09
Ahh, much better:
[http://imgur.com/IHVN.png](http://imgur.com/IHVN.png)

Thank you so very much :) !!

(I wonder why Dust 0.3.x did that?)

---

### Post by Chemical Imbalance on 2009-03-09
No problem!

Have fun theming! :)

---

