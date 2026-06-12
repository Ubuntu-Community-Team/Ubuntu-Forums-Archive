---
title: "games,dosbox"
date: 2006-11-17
forum: Gaming &amp; Leisure
---

### Post by SVDtiger on 2006-11-17
Hi im John

Im new to Ubuntu and to Linux. Being an old guy that likes games it follows that i have quite a few that would not run on that other O$

I just came back from dosbox site and found that my favs will run in Linux. Masters of Magic Master of Orion, Mechwarrior,UFO and such. 

What version of dosbox should i get for Ubuntu? or do i need it at all?

their site said Masters of Magic would run even without dosbox? im not sure of anything really but its an exciting prospect and surely a major bonus to me to maybe have use of my old games again.

much much thanks in advance

---

### Post by Carbon Based on 2006-11-17
The standard version of dosbox in the repositories should work well for the games you described. Just type this at a console:
```
sudo apt-get install dosbox
```
For older windows games, wine works very well, install it the same way, just replace "dosbox" with "wine". Both are fairly easy to use but I'd reccomend you read the manpage for each to figure out how they work. Kind of a coincidence because I'm planning on trying MOO2 on wine tonight.

---

### Post by SVDtiger on 2006-11-17
MOO is awesome (to me anyway) im sure 2 will be even better

ever play MOM? 

as far as loading them ill keep trying . im so much of a Linux noob it takes quite a bit plus im sight challenged.

you know what i had almost decided to ebay all my old games.im sure glad i did'nt now :)

thanks for the help Carbon Based. im sure ill bug you again.
have fun with MOO2

---

### Post by Carbon Based on 2006-11-17
Never played MOM, but I'll check it out. There are a ton of knowlegeable people on the forums so don't hesitate to post with questions or search. You're welcome to PM me with any problems, as well.

---

### Post by SVDtiger on 2006-11-17
Yep even as dumb as i am about all things Linux 
this forum still tries to help meh. 

Is there any MOO2 joy yet?

---

### Post by Hemmer on 2006-11-17
> **Carbon Based said:**
> The standard version of dosbox in the repositories should work well for the games you described. Just type this at a console:
```
sudo apt-get install dosbox
```
For older windows games, wine works very well, install it the same way, just replace "dosbox" with "wine". Both are fairly easy to use but I'd reccomend you read the manpage for each to figure out how they work. Kind of a coincidence because I'm planning on trying MOO2 on wine tonight.

No way! I didn't know dosbox had a linux version. :D

---

### Post by edemark on 2006-11-18
if i may suggest something i would like to call your attention on DosBoxGameLauncher (dbgl) that is a graphical user interface for dosbox, which comes with dosbox 0.65 (if i recall correctly ubuntu installs 0.63 but i might be wrong). And other than that i makes the use of dosbox extremely easy and transparent. I really like it anyway. Here is a link if you want to try it out (you mush have java 1.5 installed)
[http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/](http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/)

good gaming

---

### Post by Perfect Storm on 2006-11-18
I've played both Moo and MOM via dosbox, so it's true :)

---

### Post by SVDtiger on 2006-11-18
thank you all. this will be most cool to play the older games again. im even liking the bundled games that come with Ubuntu very much.

the screensaver that is in 6.06 that i call the cobweb conduit reminds me of an old game i have called "Delta V" where we pilot our super fast spaceship thru very much same tube attacking targets.

it was from the days of "Tie Fighter" Lucas-arts game.

Having Ubuntu now opens up a whole new realm for myself and gaming. Gamers from the old days were always very very helpful when run probs came, even back in the BBS days.

BUT Ubuntu Gamers are ever better. You guys ROCK! Much thanks and SALUTE!

---

### Post by SVDtiger on 2006-11-20
hey guys im still wanting to install Wine and dosbox.

can either or both be done from Synaptic?
i not see either app listed , of course it might be because i dont see well at all. ](*,) 

i have only used the gui in Ubuntu and as of yet, no terminal at all. 


can someone please dummy it down for me as how to install them both as i have old dos games and also win games i really want to play again.

much thanks. John

---

### Post by Perfect Storm on 2006-11-20
Then it's about time trying using command lines ;)

Here's a howto on Dosbox: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=23&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=23&Itemid=63)
Make sure your sourcelist is setup correctly.

---

### Post by SVDtiger on 2006-11-20
*shudder* i suppose so. blindguy in the china shop :O

btw im on your eyecandy page right now. awesome stuff in there.

ill go read the dosbox howto. thanks buddy, im very grateful

---

### Post by SVDtiger on 2006-12-01
> **Artificial Intelligence said:**
> Then it's about time trying using command lines ;)

well thanks to your kind guidance i think i now have both dosbox and wine also. this makes me feel a real accomplishment. Ubuntu has empowered my challemged self so much. :mrgreen: 

this is the output i got from terminal 

svdtiger@dejavoodoo1:~$ sudo apt-get install dosbox
Password:
Reading package lists... Done
Building dependency tree... Done
dosbox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
svdtiger@dejavoodoo1:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
svdtiger@dejavoodoo1:~$

will the dosbox gui function with the older dosbox version?

also can someone point me to a quick start guide for wine and the dosbox.

as always i am truely grateful, John

---

