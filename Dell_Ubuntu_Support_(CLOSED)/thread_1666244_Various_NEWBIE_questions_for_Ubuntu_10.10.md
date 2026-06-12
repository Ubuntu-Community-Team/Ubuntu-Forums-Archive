---
title: "Various NEWBIE questions for Ubuntu 10.10"
date: 2011-01-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dwnshft on 2011-01-13
Ok, so here's my predicament.
 
Computer: Dell Studio 14z (1440) laptop w/ 5gb of RAM
O.S - Dual boot (currently) w/ Win 7 and Ubuntu 10.10
 
Issues:
(1) My laptop does not detect the HDMI input from the TV when I'm trying to use my TV as an output device to play video's FROM my laptop.
 
(2) Youtube or other like sites with embedded videos don't seem to load or play.
 
(3) My Maxtor BlackArmor external hard drive will not sync with Ubuntu as its fully encrypted and does not have Linux support. Is there a work around?
 
Those are my three main issues with it right now. The third one is less of a concern right now as I can always find a non encrypted HD to use. I just have to transfer my files over IF i'm going to do a standalone Linux OS.
 
I've tried searching and haven't found anything that directly answers these specifcially. I'm not a programmer but I can pick up on things quick.
 
Thanks in advance.

---

### Post by marin123 on 2011-01-13
(1) what video card do you have and do you have proprietary drivers installed? go to: System -> Administration -> Additional drivers

(2) did you install restricted extras? you dont seem to have flash player installed. open terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Dwnshft on 2011-01-13
> **marin123 said:**
> (1) what video card do you have and do you have proprietary drivers installed? go to: System -> Administration -> Additional drivers
 
(2) did you install restricted extras? you dont seem to have flash player installed. open terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```
 
I will have to check on the additional drivers when I get in. I know its a Nvidia video card but I couldn't tell you specifically what it is.
 
I have tried installing the updates whenever Firefox asked me to ... but then it keeps saying that its not installed. :confused:
I will also check the restricted extras thing when I get in.
 
Are there any other issues or recomendations anyone has for me. I really enjoy the simplicity of Ubuntu...its kinda like if Apple and Android gave birth to they're own O.S. lol
 
Also, would anyone recommend any web browser over the next? I'm used to running Google Chrome...never cared much for Firefox.

---

### Post by marin123 on 2011-01-13
i use chrome (not chromium) and i like it better then ff (mainly because it doesnt have window bar on top, just the tabs), and i think it has its own flash player which works great :)

---

### Post by Dwnshft on 2011-01-13
Did you download that one from the market or directly from Google? I believe I got the Chrome stable...but again, I'll have to check.
 
Man, I really hope I'm making the right decision by switching to Linux. lol

---

### Post by marin123 on 2011-01-13
i think i downloaded from google. i have their repository in my software sources so i get updates every now and then. i'm using stable release.

you are doing the right decision, you will see in time that ubuntu is way better then windows, and its going to be better in time, because its evolving as we speak.

i have windows 7 on my machine and i rarely use it, just if i want to play a game or something.

these forums are great for learning about ubuntu and computers, i found a solution for every problem i have had.

think like this: if ubuntu fails, you can get back to windows, so in the end, you dont lose anything (if you have large enough external hdd :D ), but if ubuntu suits you, you will gain.

---

### Post by Dwnshft on 2011-01-18
:pOk, So i've gotten a few of my issues resolved and I have some more info to help get me some answers.
 
I still haven't figured out the HDMI output issue...but I checked and my video hardware is listed as NVIDIA MCP79MX. I've been to the Nvidia site and I can't even see what family that is part of. 
 
I am also having an issue with Vuze...installed the one from the download centre (I think its 4.3 or something) and everytime I try a search the little search astrics just blinks at me...So, I downloaded the new version of Vuze but its not a install/executable file. I'm still very new to linux and haven't learned how to install those types of files...I've just read something about opening a shell and typing something into a terminal...geez...:p
 
Any chance I can get a dumbed down walk through?

---

