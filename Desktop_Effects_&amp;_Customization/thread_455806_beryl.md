---
title: "beryl"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by sethdotcom on 2007-05-27
finally got it running but I am having one little problem with it , i cant see the bars on top of the windows


here is a screen shot of my problem

[http://i7.tinypic.com/5yi9afs.png](http://i7.tinypic.com/5yi9afs.png)

---

### Post by sethdotcom on 2007-05-27
finally got it running but I am having one little problem with it , i cant see the bars on top of the windows


here is a screen shot of my problem

[http://i7.tinypic.com/5yi9afs.png](http://i7.tinypic.com/5yi9afs.png)

---

### Post by mengfei on 2007-05-27
I see Emerald running in the background. Have you tried turning that off? I've found that on my laptop whenever I have compiz running, my window borders go all funky.

---

### Post by Ateo on 2007-05-27
Search the forums. This is a common issue with a common solution.

---

### Post by TigerTail on 2007-05-27
are you running a split operating system or a ubuntu only?

---

### Post by sethdotcom on 2007-05-27
> **mengfei said:**
> I see Emerald running in the background. Have you tried turning that off? I've found that on my laptop whenever I have compiz running, my window borders go all funky.

I am running a duel boot windows/ubuntu

i dont know how to turn off Emerald

---

### Post by TigerTail on 2007-05-27
try disabling the desktop effects under system/prefrences/desktop effects

my system got really buggy when i had desktop effects turned on

---

### Post by evilc on 2007-05-27
From the screen it looks like you are trying to run compiz? Change your windows to metacity or install beryl for desktop decorations. Compiz do not install all the required files needed. Change desktop effects back to normal.

---

### Post by rusty4r on 2007-05-27
> **Ateo said:**
> Search the forums. This is a common issue with a common solution.


Yes I had this problem too but it's been awhile i solved it by searching and found many others had it too, good luck

---

### Post by sethdotcom on 2007-05-27
When i disable destop effects everything goes back to normal is there anyway to get this to work right?

---

### Post by ryanVickers on 2007-05-27
this is a common problem - here's my post on how to fix it, I made it because ther wasn't really anything good that could be found in a timely manor.

[Fix this problem]("http://ubuntuforums.org/showthread.php?t=455735")

P.S. must you torture me so with that avatar :p

---

### Post by sethdotcom on 2007-05-27
> **ryanVickers said:**
> this is a common problem - here's my post on how to fix it, I made it because ther wasn't really anything good that could be found in a timely manor.

[Fix this problem]("http://ubuntuforums.org/showthread.php?t=455735")

P.S. must you torture me so with that avatar :p
LOL i cant help it i am a mac/windows/linux guy

---

### Post by ryanVickers on 2007-05-27
where's the mac in that picture! :)  Why would anyone who uses a mac ever touch windows anyways!  office works on mac, so does openOffice.org, and you could run your games if you want using wine or something.  :)  Speaking of which,... never mind, I'll make another post for that!  anyways!...

back to the point, did you try my advice and if so did it work?

---

### Post by janascii on 2007-05-27
There are a number of possible things that could cause beryl and/or compiz to go crazy.  I had the same problem and so did my roommate when he first installed ubuntu.  First, make sure that the line
> Option "AddARGBGLXVisuals" "True" 
is in the screen section of your xorg.conf file.

Next, make sure that your graphics are set to 32 bit color.  I have Nvidia so this might be different than ATI(I gave up on them), but open the Nvidia settings dialog in Applications -> System Tools menu.  you should be able to find it from there.

Also I must note... Emerald is the beryl theme manager.  I wanted to make this clear, but you can run beryl without it.  Beryl will just use the standard GTK window decorator and the window borders will look like normal Gnome.  

This is about all I can help with without any detailed information.  Good luck

---

### Post by sethdotcom on 2007-05-27
> **ryanVickers said:**
> where's the mac in that picture! :)  Why would anyone who uses a mac ever touch windows anyways!  office works on mac, so does openOffice.org, and you could run your games if you want using wine or something.  :)  Speaking of which,... never mind, I'll make another post for that!  anyways!...

back to the point, did you try my advice and if so did it work?



I run OS X on my secondary machine it is a Imac g3 not that fast, On my main machine where i am having the problem I run windows XP/Ubuntu dual-boot

I  have to have windows for my business, I have alot of windows only apps I need to run
I use linux and mac for fun and Windows for work.

---

### Post by ryanVickers on 2007-05-27
Wierd, I would have done the oposite, windows for fun just because all the games are for it, and work on linux and mac because you can actually trust it!  But I bet an old G3 is still faster than a brand new computer that's been running vista for say, 3 months :)
(also, I wouldn't touch vista with a 39.5 foot poll) :)

Again, did it work, or have you tried my advice yet!?

---

### Post by LastHylian on 2007-05-27
Try right-clicking on your Beryl icon and going to select window manager and and clicking Beryl. If that doesn't work, try looking at a few different Emerald themes to make sure it isn't just that one. I'm kinda in a difficult situation with Beryl myself ^_^

---

### Post by ryanVickers on 2007-05-27
Are you talking to me?  I don't know, mine's working! :lolflag:

anyway, I hope everyone get's there effects working!

---

### Post by sethdotcom on 2007-05-27
> **ryanVickers said:**
> Wierd, I would have done the oposite, windows for fun just because all the games are for it, and work on linux and mac because you can actually trust it!  But I bet an old G3 is still faster than a brand new computer that's been running vista for say, 3 months :)
(also, I wouldn't touch vista with a 39.5 foot poll) :)

Again, did it work, or have you tried my advice yet!?

I dont play many games 

and yes my imac g3 is way faster than running vista on my main machine 

I cannot believe how much vista slows down my machine, xp and ubuntu are blazing fast on it even when running beryl, I never see any down-time

but when it comes to vista it is hell
Microsoft needs to take some lessons from linux
ohhhh well .......................hopefully Apple and linux gain some more market share
we are on the way tooo, with dell releasing ubuntu on there machines and  Apple switching to intel

---

### Post by ryanVickers on 2007-05-27
It's true!  When prople realize that on a $500 computer they can save like $250 by not getting wondows, they're gonna think "hmm, what's this ubuntu thing" and it'll spred like wildfire!  HA HA HA!!!

*cough*
ahem, anywhays, yeah micr$oft is going to be facing some tough times in the next 10 years!

---

### Post by sethdotcom on 2007-05-27
> **ryanVickers said:**
> It's true!  When prople realize that on a $500 computer they can save like $250 by not getting wondows, they're gonna think "hmm, what's this ubuntu thing" and it'll spred like wildfire!  HA HA HA!!!

*cough*
ahem, anywhays, yeah micr$oft is going to be facing some tough times in the next 10 years!

lets just hope

---

