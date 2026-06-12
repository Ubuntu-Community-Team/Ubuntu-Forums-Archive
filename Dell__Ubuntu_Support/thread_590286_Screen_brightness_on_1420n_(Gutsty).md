---
title: "Screen brightness on 1420n (Gutsty)"
date: 2007-10-24
forum: Dell  Ubuntu Support
---

### Post by Kalli on 2007-10-24
After I upgraded to Gutsy when I haven't touched the computer for a minute or so the screen brightness dims down, it however does not brighten up again once I start using it again so I have to do it manually. This only happens when I'm using the battery, not when it's plugged in.

Anyone else experiencing this and/or know a fix?

---

### Post by ebe326 on 2007-10-24
Same thing happening here. I don't have a fix but I did disable the dimming so now it just doesn't dim at all. Go to System>Preferences>Power Management. Click the 'On Battery Power' tab, uncheck 'Dim display when idle' and set 'Dim display brightness by' to 0%.

david

---

### Post by bluedragon436 on 2007-10-25
Apparently this is a power option that they thought was an option that was worth having.  I noticed this the first time after I set my 7.10 up.  It was actually too dark to even notice that it was running in the first place...I just deactivated it, as I am not too worried about it "killing" my battery in the five seconds it is left alone.

---

### Post by Kalli on 2007-10-25
Yeah thanks, hadn't even thought of that. Does just fine for me having it disabled :)

---

### Post by frbe0101 on 2007-10-25
Weird, because it goes back to normal brightness on mine (it works),  What were the power management settings when you get this anomaly? You had it dim when plug in but idle right?

---

### Post by Kalli on 2007-10-28
I hadn't touched the settings, I think it doesn't dim when idle by default when it is plugged in...not sure

---

### Post by raxso on 2007-11-02
Got this problem also when it is idle for about 1 minute the screen becomes dim, but it seems that even i am using it and i am just using the battery the screen is dim but when i use AC power it works fine the screen is ok. Im using inspiron 6400 this does not happen when i use Feisty.

---

### Post by Linicks on 2007-11-02
Refer to my bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/159336](https://bugs.launchpad.net/ubuntu/+bug/159336)

Nick

---

### Post by liquidpele on 2007-11-05
Okay, so here is the deal on this.

Gibon sets the screen brightness when on battery power so low that you can barely read the screen.  

To change this, go to System -> Preferences -> Power Management

Now here is the tricky part.

On the "On AC Power" tab, set the brightness to 100%

On the "On Battery Power" tab, you don't set the brightness, but instead you set the % you want it to DIM, in relation to the brightness set in the "On AC" tab. 

In other words, if you set the "AC" tab to 50% brightness and then set the "Battery" tab to dim by 50%, you're battery will be on 25% of it's maximum brightness when on battery power.

I set mine to 100% for AC, and 20% for Battery, but you can play with it to adjust to whatever you want.

---

### Post by Linicks on 2007-11-05
Yes, that algorithm works, but it's still ares-about-tit as far as I am concerned.  The slider does say 'dim when on battery' not 'percentage of the AC brightness to dim by'.

Nick

---

### Post by TheRoot on 2007-11-18
> **liquidpele said:**
> Okay, so here is the deal on this.

Gibon sets the screen brightness when on battery power so low that you can barely read the screen.  

To change this, go to System -> Preferences -> Power Management

Now here is the tricky part.

On the "On AC Power" tab, set the brightness to 100%

On the "On Battery Power" tab, you don't set the brightness, but instead you set the % you want it to DIM, in relation to the brightness set in the "On AC" tab. 

In other words, if you set the "AC" tab to 50% brightness and then set the "Battery" tab to dim by 50%, you're battery will be on 25% of it's maximum brightness when on battery power.

I set mine to 100% for AC, and 20% for Battery, but you can play with it to adjust to whatever you want.

Wow ...
Thanks mate, really this was a clever notice from you ...
I really appreciate it :)

---

### Post by rosegarden78 on 2008-01-19
Try typing the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

