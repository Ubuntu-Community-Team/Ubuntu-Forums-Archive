---
title: "help me stay focused !.!"
date: 2011-03-15
forum: Desktop Environments
---

### Post by tawalaya on 2011-03-15
Hi,
I got a little question. I want to disable any input from my keyboard and/or mouse for a set time. So that I only can see what is on the screen at that moment, without the ability to change it for that set time, it also would be perfect if I could disable any notifications form ubuntu during that time.  Some idea how?

I need this to focus really hard on one thing at the time. If the thing with the keyboard it to hard to do, it there a way to make sure that one window is visible for the set time without a way to minimize it or switch to another window? 

I thinking about making a script for that mode that only needs the time in seconds or so. Sadly I wasn't able to find any good references on the internet so far, hopefully you guys can help me ;) 

BIG THANKS for that! 
if you have any other tips on how to stay focused on one thing on the screen without wandering of to Facebook or other things that would be great ;) thanks.

---

### Post by nicolasdiogo on 2011-03-15
did you see this?
[http://ubuntuforums.org/showthread.php?t=604134](http://ubuntuforums.org/showthread.php?t=604134)

---

### Post by Grenage on 2011-03-15
> **tawalaya said:**
> if you have any other tips on how to stay focused on one thing on the screen without wandering of to Facebook or other things that would be great ;) thanks.

This is one of those classic cases where technology is no substitute for mental discipline.  While it may be a temporary and situation-specific fix, it won't help you with anything else down the line.

If you can set time periods for work and play, it will help, but you'll still have to force yourself to stick to it; it gets easier over time.

---

### Post by tawalaya on 2011-03-15
Oh thats a good start! any idea how i can add the timer function I was talking about? I am not so good with perl ~.~ never used it before :P

---

### Post by tawalaya on 2011-03-15
> **Grenage said:**
> This is one of those classic cases where technology is no substitute for mental discipline.  While it may be a temporary and situation-specific fix, it won't help you with anything else down the line.

If you can set time periods for work and play, it will help, but you'll still have to force yourself to stick to it; it gets easier over time.

I guess you are right, the thing is that all those notifications and tempting little things that all of us have on our computers can be distracting from time to time thats why I thought to my self why not forbid myself from using those for a few minutes. That way I can get more used to it and over time may don't need it anymore ;)

---

### Post by tawalaya on 2011-03-15
Hi again, i have found a program that dose what I wont at least half way. It is called **xtrlock**. Found at after knowing the right keyword to go for ;) 

So now the question how to I get it to work the way i need it to? Since i wont a timer and all ;) I got a idea but don't know exactly how to do it. Hear it goes : I wont to write a script with bash that calls xtrlock and than kills it after set time. 

How do I do it?

Lastly how can I disable and enable the ubuntu notification system using the command line or using my little bash script?

[UPDATE]
Only need help with the notifications now, get my script Working!

```

#!/bin/bash
if [ -z "$1" ] 
then
  t=60
else
  t=$1
fi
exec xtrlock & echo "locked for ${t}s" & 
sleep "${t}"s && echo "unlock" && killall -9 xtrlock

```

hope it hels someone ;)

---

### Post by stinkeye on 2011-03-15
Have a look at the forced typing break function in preferences > keyboard .

---

