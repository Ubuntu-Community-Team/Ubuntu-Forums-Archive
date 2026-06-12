---
title: "Nvidia-settings and XGL"
date: 2006-12-17
forum: Desktop Environments
---

### Post by sarikan on 2006-12-17
Hi, 
I have managed to configure xubuntu-desktop with xgl, however, I can't get nvidia-settings to work so that I can adjust brightness and gamma
Is there a way to get it work under xgl? (my eyes hurt...)

Regards

---

### Post by aidanr on 2006-12-17
yeah, without direct rendering a lot of the options don't show up. if you can, update to the latest nvidia drivers, they have an implentation of aiglx built in which you can use with beryl (compiz i'm not so sure about) and still have direct rendering

---

### Post by sarikan on 2006-12-17
Hmm, 
I am using compiz, but from what I have read beryl is a little bit immature at the moment? I was doing fine with compiz :(
I think I'll start with updating the nvidia drivers, and check beryl out if I feel like it. Is not there any way to change brightness contrast gamma using XGL settings?

Regards

---

### Post by aidanr on 2006-12-17
sorry, just looked it up, it's been months since i've used compiz, nvidia's implementation does work with compiz
[http://forum.go-compiz.org/viewtopic.php?t=90](http://forum.go-compiz.org/viewtopic.php?t=90)

---

### Post by sarikan on 2006-12-17
Thanks for taking the time to check it out; but I am not sure I get what you mean exactly. At the moment I have nvidia drivers, compiz, and xgl. 
To make nvidia-settings work; would updating nvidia drivers be enough? The page you have provided shows installing compiz from ground up, but that'd probably make things a little bit complicated for me. 
Do you think only updating the drivers solve my issue? The problem seems to be that nvidia-settings looks for some extensions but xgl does not provide them. Do you think that Updating the drivers for nvidia would fix this? Or am I getting the cause of the problem wrong?

---

### Post by aidanr on 2006-12-17
yes if you update the nvidia drivers and make the changes mentioned to /etc/X11/xorg.conf (make sure to backup) then compiz should use the nvidia drivers instead of xgl. i'm not sure if compiz will choose nvidia over xgl automatically though, beryl does as far as i know and also the beryl system tray icon allows you to switch between xgl/nvidia/aiglx, i don't know how compiz handles this, maybe someone else can clarify or you could ask on the compiz forum

---

### Post by sarikan on 2006-12-17
Oh, I get it know! So the new driver includes the functionality of xgl. Hmm, this means a little bit of a change in the way I make things work, but it looks like a good shot. 
Aside from my problem, this is an interesting issue; would this move by nvidia make xgl used less? Why would the nvidia users choose xgl over nvidia drivers in this case? 
I assume this new driver would also enable use of opengl in games under compiz or beryl also (which, according to my knowledge is not possible at the moment)

---

### Post by aidanr on 2006-12-17
as far as i can tell xgl was made by novell and it was mostly done in private and without community involvement, so then aiglx was made by the community which was less of a hack and better written code, and then nvidia included their implementation of aiglx in their drivers

now seeing as i have an nvidia card and need nvidia drivers anyway, it makes more sense to me to use the nvidia drivers rather than to have aiglx installed aswell

now xgl uses indirect rendering which is slow for opengl games and such, and aiglx/nvidia uses direct rendering which is faster

**disclaimer:** bear in mind this is what i understand from my limited knowledge on the subject;)  check wikipedia or somewhere for more solid facts

so as for opengl games, well it certainly is possible to play them with xgl, you just need to run them in a seperate normal x server, but with aiglx it's a lot easier, but bear in mind that it is still worth killing beryl or compiz before you start your game as you will get better framerates with those turned off, afterall  if it is on while you are running your game, it's like having two opengl applications using the graphics card

theres a few threads about how to write a simple script to shutdown compiz/beryl while you're running your game for example my ut2004 launcher looks like this:

#!/bin/bash
killall beryl &&
cd /home/aidan/games/ut2004/
./ut2004 $1 &&
beryl &

so when i click the ut2004 icon, it stops beryl, starts ut2004 and when i quit ut2004, beryl starts up again

---

### Post by sarikan on 2006-12-18
Thanks for the info. At the moment, I have latest nvidia drivers, but whatever the version of compiz I install, I have problems. If I install using this repositories:

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

I get the black screen problem, where only the top bar appears and all other things looks black, I still have some kind of screen (at least I can see the mouse cursor)

However, If I use this repository for freedesktop packages: 

deb [http://gandalfn.club.fr/ubuntu/](http://gandalfn.club.fr/ubuntu/) dapper .

All I get is a dead screen. By dead I mean like the one you get when your monitor powers off. So far I could not find out how to deal with it. Do you have any idea about what should the repositories be for dapper?
I am really stuck :(

Regards

---

