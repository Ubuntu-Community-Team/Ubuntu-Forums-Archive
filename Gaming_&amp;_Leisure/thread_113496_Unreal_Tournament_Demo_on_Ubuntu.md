---
title: "Unreal Tournament Demo on Ubuntu"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by hardsteel on 2006-01-06
Doesn't seem to work.. sob. The splash screen comes up and dissapears some time later. What's the deal?? I wanna get it working! Plz help!

---

### Post by Lord Illidan on 2006-01-06
It works on mine. What hardware do you have? Did you install it correctly? Try launching it from the terminal to see what errors it gives you.

---

### Post by hardsteel on 2006-01-06
Well, i've  got dell latitude CPx laptop. What hardware u mean?
I've got pentium 3 500 mhz, ati mobility 8 mb

I know it's slow but it worked very good in windows!

What is the command for launching it? 

I installed it by unpacking the .tar.gz with the archive manager etc.....

---

### Post by Nomearod on 2006-01-06
I have another problem...

The demo runs, but the full game doens't...

---

### Post by hardsteel on 2006-01-07
Doesn't anyone else have anything to say?? :(

---

### Post by Perfect Storm on 2006-01-07
Did you install it as super user do? (sudo)
Do you have /.ut2004 in /home/<username>  ?

---

### Post by hardsteel on 2006-01-07
It is UT '99 not 2004.  :( I installed it by simply exctracting ...

---

### Post by Perfect Storm on 2006-01-07
Any terminal output when running it there?

---

### Post by hardsteel on 2006-01-07
err.. what?? Soz, im noob in linux...

---

### Post by Perfect Storm on 2006-01-07
How do you try to run the game? Do you click on an icon which says UT?

---

### Post by hardsteel on 2006-01-07
There is a file called UnrealTournament in the \System dir.
In win, its .exe and that's the file I use to load the game in win

---

### Post by Perfect Storm on 2006-01-07
Try drag the file you start UT into the terminal and press enter, please post the output of it.

---

### Post by hardsteel on 2006-01-07
Dragging didn't help much. Instead I did 

cd Desktop\utdemo\System
./unrealtournament

And that's what happened:

cp: stat `/home/mattias/.utconf' ei õnnestu: No such file or directory
gd error (glide): Can't find or access Banshee/V3 board
Aborted
mattias@ubuntu:~/Desktop/utdemo/System$

---

### Post by hardsteel on 2006-01-08
Can anyone in here help me out? :(

---

### Post by Stroganoff on 2006-01-08
I got the same problem. The README states, that there is no MesaGL-Support yet but only 3dfx-Glide.
Is there a way to get Glide working on a Geforce4?

---

### Post by slux on 2006-01-08
The UT demo is very dated and you won't get it working with anything except glide as the error message indicates. Sorry, I don't think there's a way to get Glide on a Geforce in Linux. The full version of UT does have the required OpenGL driver though.

---

### Post by hardsteel on 2006-01-08
i already playing ut full with wine. It also ran the demo nicely.. 

Soon im gonna get the ut installer from liflg.org and enjoy it without wine



 :cool: :cool: :cool: :cool: :cool: :cool: :cool: :cool:

---

