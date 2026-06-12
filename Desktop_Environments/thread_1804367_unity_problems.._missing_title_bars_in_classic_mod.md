---
title: "unity problems.. missing title bars in classic mode, no desktop cube etc etc etc."
date: 2011-07-14
forum: Desktop Environments
---

### Post by crshbndct on 2011-07-14
i just recently got back from an overseas holiday, and decided to update my ubuntu.

how i wish i had never done this!!
i used to run docky, (which still works) and desktop cube, wobbly windows, beam effects etc. i loved how much eye candy there was.

but i also like new things, so i upgraded my system to 11.04 when i turned it back on, and i absolutely hate the new interface. i can see how it might be better for a linux virgin, but its kinda frustrating having all the stuff that i was used to using and showing off to my friends missing.

so i decided that i would just try classic mode, which still doesnt work. no title bars, desktop cube still send my pc into a spin which requires a hard reset, and there are just too many conflicts between compiz and unity for my liking.
but now i am stuck with this new thing and i dont know how to rollback to 10.10 without a format.

i have convinced quite a few people with pentium 4ish hardware to use ubuntu rather than upgrading, and they are all true believers now, but i suspect that they are going to be very annoyed that all their special effects are gone.

---

### Post by wildmanne39 on 2011-07-15
> **crshbndct said:**
> i just recently got back from an overseas holiday, and decided to update my ubuntu.

how i wish i had never done this!!
i used to run docky, (which still works) and desktop cube, wobbly windows, beam effects etc. i loved how much eye candy there was.

but i also like new things, so i upgraded my system to 11.04 when i turned it back on, and i absolutely hate the new interface. i can see how it might be better for a linux virgin, but its kinda frustrating having all the stuff that i was used to using and showing off to my friends missing.

so i decided that i would just try classic mode, which still doesnt work. no title bars, desktop cube still send my pc into a spin which requires a hard reset, and there are just too many conflicts between compiz and unity for my liking.
but now i am stuck with this new thing and i dont know how to rollback to 10.10 without a format.

i have convinced quite a few people with pentium 4ish hardware to use ubuntu rather than upgrading, and they are all true believers now, but i suspect that they are going to be very annoyed that all their special effects are gone.Hi, first you shoud look at this link it is for compiz in classic.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)
You might want to check and see if you have the unity plugin checked in classic because you do not need it checked and I it would cause some of your issues.

---

### Post by crshbndct on 2011-07-16
thanks i will try that.
i decided to try kubuntu but that was a nightmare of epic proportions

---

### Post by wildmanne39 on 2011-07-16
> **crshbndct said:**
> thanks i will try that.
i decided to try kubuntu but that was a nightmare of epic proportions
Hi, ok and after you get it fixed you can use this guide to setup the cube and effects it has pictures for every step.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by pritam_par on 2011-07-31
[FONT=Arial][SIZE=2]Enabling Cube with unity will kill the unity. This can be solved just follow the process below

1.In compiz setting manager disable these plugin:
[/SIZE][/FONT] [FONT=Arial][SIZE=2]            i) OpenGL[/SIZE][/FONT]
[FONT=Arial][SIZE=2]            ii) Composite[/SIZE][/FONT]
[FONT=Arial][SIZE=2]            iii) Ubuntu unity plugin[/SIZE][/FONT]
[FONT=Arial][SIZE=2]           iv) Desktop wall.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    Select ***disable plugins*** when a window appears asking for disabling other plugins.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]After disabling these plugins your panels and unity will disappear,don't panic and follow next step.

2. Now enable these plugins sequentially. [/SIZE][/FONT]  
[FONT=Arial][SIZE=2]        i)OpenGl[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       ii)Composite[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]      iii)Desktop cube [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]      iv)Rotate cube[/SIZE][/FONT]
[FONT=Arial][SIZE=2]        v)Ubuntu unity plugin.

for title bar. Goto compiz setting manager and select **window decoration** option.
Title bar will appear again. 
[/SIZE][/FONT]

---

