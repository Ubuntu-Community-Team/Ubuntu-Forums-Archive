---
title: "A full-screen conundrum"
date: 2008-06-21
forum: Gaming &amp; Leisure
---

### Post by Tommah on 2008-06-21
Hi, I'm new to these forums and a little bit confused, so if I've posted this in the wrong section I'm sorry.

Anyway, I've got a dual-boot setup of Hardy Heron and XP, and I'm quite happy with it save for one snag.
It seems whenever I try to run anything that needs 3D acceleration (i.e. ioquake3, Unreal Tournament via Wine)in full-screen I just end up getting an "out of range" message and blank screen and have to hit the restart button. 

The weird thing is, UT runs perfectly if I run it in virtual desktop/windowed mode. Being a huge Linux newbie I don't really know how to run ioquake3 in a window, and even if I did I'd still like to try and get both programs to work full-screen.

I have an Nvidia Geforce 7600GS graphics card, and I already got the most recent drivers for it with EnvyNG, if that's any help.

Again, I'm sorry if this is in the wrong section, and if it is please move it. Also halp!

---

### Post by eragon100 on 2008-06-21
I have an Nvidia Geforce 7600GS graphics card, and I already got the most recent drivers for it with EnvyNG, if that's any help.

That doesn't help, that's the problem!

open a terminal (applications->accessories->terminal) and type:

sudo displayconfig-gtk (you can copy & paste from here)

It will ask password, type it in, it is NOT supposed to show asterisks.

In the screen that opens up, click on the box probably labeled "generic monitor" next to "model", and change it to the vendor and model of your monitor. CLick ok, restart computer and everything should work. At least, this solved exactly the same problem for me after I had installed the nvidia driver (512 MB GeForce 7 7500 LE, 20 inch Acer al2016w widescreen) :)

And by the way, Unreal Tournament has a native linux version you can download and install with the windows cdrom :)

If the resolution is messed up, go to system -> preferences -> resolution and change res. and refresh rate to something that looks good.

Have fun Playing! :popcorn:

---

### Post by diafanos on 2008-06-21
I used to have a similar problem, whenever I tried to run Enemy Territory (not via wine, but the linux version of the game).

I had to edit my **xorg.conf** file in order to solve it.

Can you post yours? it's in **/etc/X11/** directory

---

### Post by Tommah on 2008-06-22
Thanks eragon, I now have both UT and ioquake3 running in fullscreen pretty well.
But now I have another problem; this time to do with resolution.

ioquake3 loses all mouse control and switches to run in a very large window if I try to push it up to 1024x768, and UT simply will not budge from the 640x480 it was when I installed it without going to hide in the top-left corner.
I get the feeling it's because I can't get the version of my Belinea monitor *exactly* right beyond it being a 10-15-36.
Or is it that Ubuntu won't run anything larger than the desktop itself or something? 

I assume the UT thing is a Wine problem, so I'll wander off and ask about it in the Wine section. Also, I know this complaining about res is a minor detail compared to actually getting these programs to run at all, but XP has spoiled me XD
And lastly, there is a reason why I'm using Wine for UT. 
I'm considering getting an Asus Eee in a couple of months, and I'm told Wine runs UT better on one of those. Hence, getting some practice with using Wine in.

Shall I go get my xorg.conf contents anyway, diafanos?

---

### Post by eragon100 on 2008-06-22
My monitor is also set to "al2016wx" while it's a "al2016w" (no x), no problems here, so that probably isn't the problem :)

For ANY 3d game problems, I recommend disabling desktop effects;
compiz-fusion is terribly unstable with games (in fact, I don't know a single (!) linux game that doesn't have VERY serious issues, or is simply unplayable, while it's running :()

I am also going to file a bug report against the restricted drivers manager about your first issue, fullscreen, because you are the 4th person who has this problem, and this is offcourse a very serious issue: monitor is recognized, you install nvidia drivers with restricted, and the programs that should work because of that (=3d games) don't work because Ubuntu suddenly doesn't recognize the monitor anymore! :mad: :confused: :(

---

