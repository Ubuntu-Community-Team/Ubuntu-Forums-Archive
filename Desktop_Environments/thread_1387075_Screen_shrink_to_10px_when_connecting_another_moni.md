---
title: "Screen shrink to 10px when connecting another monitor"
date: 2010-01-21
forum: Desktop Environments
---

### Post by karnius on 2010-01-21
Hi guys

I have ubuntu 9.10 and when I connect another monitor, The ubuntu screen is shrinking rto 10 px.

I can move the mouse in my other monitor but everything is black (exept for the 10 px in my netbook screen),


I habe a netbook gateway with thga GAM 3150



Thank!

---

### Post by drewsus on 2010-01-21
what do you do to enable the external monitor? 
When it is black like that but you can still move your mouse it is a compiz+dualscreen set up. You can only have a virtual desktop size of 2048x2048 max with compiz. When it enables the external monitor and does so with over 1024x#### then you get this problem with compiz (cuz your netbook is already 1024x600).
What sort of monitor do you have?
Try disabling compiz, connecting and enabling the external, open a terminal and run the command:
```
xrandr -q
```
and post the output here, but also answer my other questions please.

Drew

---

### Post by karnius on 2010-01-21
I do detect monitor


I see, look like my problem, I will try that tonight and report!


I tried with a dell 24 inch and a acer 23 inch, Same problem

---

### Post by drewsus on 2010-01-21
I want to know how you detect the monitor which sets up the dualscreen environment with the black screens with moveable mouse. The method. 
xrandr manually? 
System -> Preferences -> Display?
Fn+F#?
?

Also, is it the Acer X233H 23" monitor? 
Cuz if it is... wow are you in luck haha. I just wrote a 522 line script for my girlfriend to get that working properly and sexily with muliple configuration options. She uses a Dell Mini 10v and I use an Acer Aspire One which are both netbooks. 

So, when you get a chance, answer these questions and the others etc and I will see what I can do to help you out. 

Drew

---

### Post by karnius on 2010-01-21
I do:
System -> Preferences -> Display

Is there a better method?


Yea that is my monitor!

---

