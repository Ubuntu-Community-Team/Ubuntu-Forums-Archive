---
title: "uhh... is my ubuntu 11.04 supposed to look like this?"
date: 2011-06-09
forum: Desktop Environments
---

### Post by pawan98 on 2011-06-09
Hi just installed 11.04... Is it supposed to look like this, with the side stuff on the left and things... in previous versions it weren't, im unsure. 


Also when I fully maximize my mozilla it looks weird, 

All screenshots down below.

---

### Post by dFlyer on 2011-06-09
Yes, that is unity. If you want to run gnome logout and select gnome classic at the login screen.

---

### Post by JRV on 2011-06-09
Yes, that's the new Unity user interface.
It takes some getting used to, but I learned to like it.
Read the different posts about it and you will find it is quite controversial.

---

### Post by coffeecat on 2011-06-09
It can be a bit puzzling at first, but do stick with it. Many people who have done so have come to prefer it. To help you find your way around, a couple of links for you.

Basic guide:

[http://omgubuntu.co.uk/natty/](http://omgubuntu.co.uk/natty/)

More advanced:

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

---

### Post by pawan98 on 2011-06-10
Hmm ill take a look... Now atleast I know its right. But how to fix the mozilla problem?

---

### Post by coffeecat on 2011-06-10
> **pawan98 said:**
>  But how to fix the mozilla problem?

In your OP you say it looks "weird". I've looked at your screenshot but I can't see anything out of the ordinary, except that your launcher hasn't hidden itself. This can be fixed by installing compizconfig-settings-manager and changing a setting. Instructions in one or both of those links I posted, or  if you need help with this just post back.

Or is it the max-min-close buttons in the panel? That's normal.

If I've missed something, post back, and we'll try to sort out this weirdness. :)

---

### Post by kostkon on 2011-06-10
Actually, there is something wrong in the 2nd screenshot; your firefox doesn't use the global menu for some reason.

Check if you have the package *firefox-globalmenu* installed, either check in software centre or give the following in a terminal
```
apt-cache policy firefox-globalmenu
```
the above package provides a firefox extension, so make sure that it is enabled in the firefox addons preferences.

---

### Post by pawan98 on 2011-06-10
kostkon it does use the global menu, it was just because I was using the Take Screenshoot feature you could not see it. 
 
coffecat I don't fully understand what your saying. I dont understand the launcher hasnt hidden it self. And cant i fix the minimize close and maxize error?

---

### Post by kostkon on 2011-06-10
> **pawan98 said:**
> kostkon it does use the global menu, it was just because I was using the Take Screenshoot feature you could not see it. 
 
coffecat I don't fully understand what your saying. I dont understand the launcher hasnt hidden it self. And cant i fix the minimize close and maxize error?
So, is firefox maximised in the 2nd screenshot?

---

### Post by pawan98 on 2011-06-10
Also I installed a program called unity 2d I dunno what it does but I was having problems with my driver and I installed it... What does this program do? Does it take away some features or something?

---

### Post by DinoT1985 on 2011-06-10
> **pawan98 said:**
> Also I installed a program called unity 2d I dunno what it does but I was having problems with my driver and I installed it... What does this program do? Does it take away some features or something?

Unity 2D doesn't have hardware acceleration and misses a few features.

---

### Post by coffeecat on 2011-06-10
> **pawan98 said:**
> coffecat I don't fully understand what your saying. I dont understand the launcher hasnt hidden it self. And cant i fix the minimize close and maxize error?

Let's make sure we are talking about the same thing. **If** your firefox is maximised, you can adjust a setting so that the launcher (that's the vertical strip of application icons on the left) will automatically hide. On your machine, when you maximise an application window, does the launcher hide, because in that screenshot it has not?

To your question about fixing the max/min/close buttons, if you are running Firefox maximised, there is nothing to fix. When you maximise an application window, the buttons are meant to be in the panel.

---

### Post by pawan98 on 2011-06-10
Hi again ill try all of them things when I get home however about unity 2d I want it to work without it but I don't know how... Without it the screen flickers terribly oh and my graphics card is intel 82825 gprahics controller

---

### Post by collisionystm on 2011-06-10
well if you get regular unity working, you can install the compiz config settings manager from software center and change the unity plugin. You can make the icons on the bar much smaller so it doesnt take up so much space.

---

### Post by imortalninja161 on 2011-06-10
> uhh... is my ubuntu 11.04 supposed to look like this?

yerr i was thinking the same thing when i lunched 11.0.4

---

### Post by pawan98 on 2011-06-10
I see what you mean my the unity thing should move when maximised, how do i do this?

---

### Post by pawan98 on 2011-06-11
uhh how do I do this '

                               
        add the x-swat ppa to update the intel driver 
'

---

