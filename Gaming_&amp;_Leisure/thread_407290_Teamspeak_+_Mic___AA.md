---
title: "Teamspeak + Mic  / AA"
date: 2007-04-12
forum: Gaming &amp; Leisure
---

### Post by xsprayx313 on 2007-04-12
Well, My mic won't work on TS, no one can hear me. I just installed ubuntu 2 days ago.

And Americas army, I could launch it ( but the mouse pointer would skip all over the place, and someone said to type a line into terminal... so i did and now my AA wont load at all.

---

### Post by Feba on 2007-04-12
Do you remember what the line is?

And on your mic, hate to ask the obvious, but have you made sure that the mute switch isn't on?

---

### Post by xsprayx313 on 2007-04-12
Yeah its not, cause there is no mute switch xD

I'm using Medusa 5.1 Progamers (medua-usa.com)

sudo apt-get install nvidia-glx              <---what i typed in

---

### Post by Feba on 2007-04-12
that installed new nVidia drivers... which might not be what you want. 

The mouse problem could be a driver problem with the mouse, I don't think new nVidia drivers are going to help you...especially if you don't use an Nvidia graphics card.

---

### Post by xsprayx313 on 2007-04-12
Im running an nvidia 7600 gt, audigy 4z soundcard, medusa 5.1 progamer headsets and i need mic to work in ts. not nessicarily the AA to work, ill dual boot for that.. but ts needs to work properly.

btw theres possibility about the mouse driver, i know that the website  [www.razerzone.com](www.razerzone.com) doesnt have any linux drivers for installation.. maybe i can run the drivers installation under wine? idk  but i'll get the cd, i doubt that would do anything though, as the site has no drivers for linux =\

---

### Post by Feba on 2007-04-12
If your mouse doesn't have driver support for linux, that could be the cause of your problems.

---

### Post by xsprayx313 on 2007-04-12
Im seriously doubting that my mouse not having drivers makes my mic not want to work.

---

### Post by Feba on 2007-04-12
I'm referring to your problems in AA.

---

### Post by xsprayx313 on 2007-04-12
Don't worry about them now, I dont really want to play AA on linux now, i figure too many problems.. i lll dual boot to XP for that, really need the ts tho.

---

### Post by xsprayx313 on 2007-04-12
bump :P

---

### Post by lakersforce on 2007-04-12
install the "alsa-oss" package and run both AA and Teamspeak from a commandline with "aoss" before them (for example "aoss AA" and "aoss teamspeak"). That should solve your problems.

---

### Post by xsprayx313 on 2007-04-12
i dont want to play AA, i dont have any drivers for my mouse on linux, my soundcard doesnt have any linux drivers and niether does my video card.  so anyone know how to make my mic work.

---

### Post by Feba on 2007-04-13
> install the "alsa-oss" package and run both AA and Teamspeak from a commandline with "aoss" before them (for example "aoss AA" and "aoss teamspeak"). That should solve your problems.Did you even try this?

---

### Post by xsprayx313 on 2007-04-13
I would if i wanted to play AA

---

### Post by Feba on 2007-04-13
> ** install the "alsa-oss" package and run** both AA and **Teamspeak from a commandline with "aoss" before them** **(for example **"aoss AA" and **"aoss teamspeak"). That should solve your problems.**So i'm guessing you didn't even read it?

---

### Post by xsprayx313 on 2007-04-13
if i wnated to i wouldnt even know how.

---

### Post by lakersforce on 2007-04-13
```
sudo apt-get install alsa-oss
```
this will install the alsa-oss wrapper which you need if you want to have sound in two programs at once (ie. teamspeak and whatever game you want to use it with).


[quote=xsprayx313]I would if i wanted to play AA[/quote]
you where the one who said you wanted to play AA.


[quote=xsprayx313]if i wnated to i wouldnt even know how.[/quote]
Ehh...you mean you cant read...? You already showed you know how to use apt-get and to run things from a commandline, so whats the problem?


To install your video-driver:
```
sudo apt-get install nvidia-glx
```


To enable your video driver:
```
sudo nvidia-glx-config enable
```
and
```
sudo dpkg-reconfigure xserver-xorg
```
and choose the "nvidia" setting instead of "nv".


As for your soundcard, I dont know. I have never heard of a soundcard that is not supported by default by Ubuntu. Sometimes Ubuntu does not find the sound hardware on boot-up and a second (and sometimes a third and even fourth) boot is required.


As for your mouse problems, your mouse should work fine if it is a usb mouse. If it is a ps/2 make sure you have connected it to your mouse port and not your keyboard port (this might sound stupid, but contrary to Windows it does make a difference in linux (or is it the other way around? I cant remember!)).


If you follow these guidelines, everything should be running fine in no-time. But dont be afraid to post your problems if it dont.

---

### Post by xsprayx313 on 2007-04-13
The mouse i wouldnt play AA with because the drivers dont come for linux, and that is bad because the mouse is a 2000psi mouse so it can get really sensitive, which is what im use to... but now its not sensitive at all with out the drivers...

---

### Post by lakersforce on 2007-04-14
Somewhere else in this forum there are links to guides to do all kind of things with your mouse. I dont remember where though, so you will have to find it yourself.
But I am sure, even though there is no drivers for your mouse, you can tweak the appropriate files to make it behave excactly like you would want it to. If you tweak it right you can proberly make it behave better and more sensetive than in windows.
But always remember to take back-up of important systemfiles before you begin tampering with them!

---

