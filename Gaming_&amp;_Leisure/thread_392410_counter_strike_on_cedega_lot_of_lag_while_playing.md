---
title: "counter strike on cedega: lot of lag while playing"
date: 2007-03-24
forum: Gaming &amp; Leisure
---

### Post by r0ck80y on 2007-03-24
Hi,

Recently i installed cedega and then counter strike. I was able to play on lan but there's a lot of lag as i move. Its kinda like zip ahead a few metres and then stop, then zip again, stop and so on....
I disconnected from the lan game and started my own game with no players except me. There was no lag this time but instead i was running at twice the normal speed. All cedega video and audio tests pass without any problems; however the gears in the animation are rolling at great speeds !!!!

Any ideas what is happening?? :confused:

---

### Post by lordhebe on 2007-03-24
> **r0ck80y said:**
> Hi,

Recently i installed cedega and then counter strike. I was able to play on lan but there's a lot of lag as i move. Its kinda like zip ahead a few metres and then stop, then zip again, stop and so on....
I disconnected from the lan game and started my own game with no players except me. There was no lag this time but instead i was running at twice the normal speed. All cedega video and audio tests pass without any problems; however the gears in the animation are rolling at great speeds !!!!

Any ideas what is happening?? :confused:

It's down to CPU scaling, the program detects the CPU speed at it's passive state (in power-saving mode) but then it speeds up, and thus the game speeds up. To solve this issue type in a terminal (as root) 

```
/etc/init.d/powernowd stop
```

This has to be run in a terminal every time you load up your computer.  I make a script and put it in my home folder, meaning all i have to type is:

```
sudo sh nowd
```

This solution worked for me perfectly :guitar:

---

### Post by r0ck80y on 2007-03-26
Hey, thanks!! that worked !! :) 

Another thing....I get fps of 50 or less ( sometimes 60) while playing but abt 120+ when i am spectating. I keep all  processes to a minimum ( run the game in fluxbox); and i cant clearly understand the graphics options in cedega. I have also submitted the various commands in the game console that supposedly help in increasing fps. How do i increase the fps while playing??

( In windows i had turned off vertical sync through nvidia and that brought about a major increase in the fps. Is there a similar tweak for linux, in xorg.conf maybe :| )

---

