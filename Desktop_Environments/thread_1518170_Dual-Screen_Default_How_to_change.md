---
title: "Dual-Screen Default? How to change?"
date: 2010-06-26
forum: Desktop Environments
---

### Post by Terrum on 2010-06-26
Sorry if this is the wrong place to post this. There was a little too many to choose from considering the issue.

Anyway, I think you can see by the image what's wrong.

[[IMG]http://img535.imageshack.us/img535/1755/pict0235y.jpg](http://img535.imageshack.us/i/pict0235y.jpg/)

Everything is on my secondary (left) monitor. I want my primary (right) monitor to have the toolbars and default stuff on it. Is it possible? I haven't seen it on the settings and I've searched around but all posts are like 2007-2008 which have different layouts of solutions which don't work or aren't the same. Thanks.

---

### Post by matt-fender on 2010-06-26
If i remember correctly you go to System > Preferences > Monitors

Then drag the boxes to match your  desk  configuration??

---

### Post by Terrum on 2010-06-26
> **matt-fender said:**
> If i remember correctly you go to System > Preferences > Monitors

Then drag the boxes to match your  desk  configuration??
Nope because the boxes are matched already to the monitors on my desk (And the mouse moves from screen-to-screen normally)

What I mean is I want the bars (the clock, buttons, etc) to be on my right monitor and not my left.

Thanks for your reply.

---

### Post by matt-fender on 2010-06-26
> **Terrum said:**
> Nope because the boxes are matched already to the monitors on my desk (And the mouse moves from screen-to-screen normally)

What I mean is I want the bars (the clock, buttons, etc) to be on my right monitor and not my left.

Thanks for your reply.

Ah i see i apoligize lack of sleep :/ So you need to switch your PRIMARY monitor?

---

### Post by matt-fender on 2010-06-26
Try running "xrandr" in terminal, see what monitors are what and then try changing

xrandr --output HDMI1 --primary
to fit your needs

Failing that [http://ubuntuforums.org/showthread.php?p=9489366](http://ubuntuforums.org/showthread.php?p=9489366) post #5 looks helpful

---

### Post by nelylcona on 2010-06-26
Alright, I am new to ubuntu, not linux. 
As i love running dual monitors. I ran into the same problem with the new Ubuntu....

My solution; 
I was running both my monitors with the default monitor settings. I then updated the hardware for Nvidia...
THE update made my monitors none functional, PLUS the Nvidia system sucked.... It was suppose to be able to run better color and better resolution. 


My question for you, Which version of ubuntu are you using??? Do you have a Nvidia video card???

---

### Post by matt-fender on 2010-06-26
By default the left monitor is set to primary in ubuntu, the xrndr commands should allow you to change this the other way round

---

### Post by Terrum on 2010-06-27
> **matt-fender said:**
> Try running "xrandr" in terminal, see what monitors are what and then try changing

xrandr --output HDMI1 --primary
to fit your needs

Failing that [http://ubuntuforums.org/showthread.php?p=9489366](http://ubuntuforums.org/showthread.php?p=9489366) post #5 looks helpful
I will try that, thanks alot.
> **nelylcona said:**
> Alright, I am new to ubuntu, not linux. 
As i love running dual monitors. I ran into the same problem with the new Ubuntu....

My solution; 
I was running both my monitors with the default monitor settings. I then updated the hardware for Nvidia...
THE update made my monitors none functional, PLUS the Nvidia system sucked.... It was suppose to be able to run better color and better resolution. 


My question for you, Which version of ubuntu are you using??? Do you have a Nvidia video card???
Latest version of ubuntu and I've got an ATI Radeon HD 4850
> **matt-fender said:**
> By default the left monitor is set to primary in ubuntu, the xrndr commands should allow you to change this the other way round
Thanks I will try that.

EDIT: The update facility that comes with Ubuntu updated my video drivers and gave me an ATI control panel. I used that for the dual-screen defaulting and it works perfectly now! Thanks alot for all your help

---

