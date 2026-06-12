---
title: "PPSSPP - PSP Emulator. Ubuntu 12.04, Need Help Installing"
date: 2013-07-16
forum: Gaming &amp; Leisure
---

### Post by brantpadams on 2013-07-16
Here's a link to the site for [PPSSPP]("http://www.ppsspp.org/downloads.html"). They have a lot of videos and HD screenshots available as well.

It's really a solid emulator and it's gone through a lot of very nice performance updates. I've got it running relatively smooth on my HTC EVO 4G LTE and I really like it. To my knowledge, they had a 32-bit version of it available for download on Linux, but now they just have a link that's supposed to take you to builds which I'm not sure works anymore. I did find a guy who has it running [here]("https://www.youtube.com/watch?v=LELEwJM5eOs"), but I'm not fairing too well with his instructions via Google translate. 

I'd really just want to install this on my laptop. I have a Dell Inspiron 1525 32bit, and when I heard this was 32bit compatible I really wanted to try it. The video link above has links to his instructions on how to get it working, but I've yet to figure it out. If anyone here has already had experience with this emulator, I'd really love some help. I'm a pretty big novice when it comes to actually doing builds so I would need very straightforward instructions on how to do it. No rush of course, it's just games. :)

Thanks in advance.

---

### Post by Lightning Dragon on 2013-07-16
Hi,

First, you need to install the SDL library. 

*sudo apt-get install libsdl1.2-dev*

Download the Linux pack after and then you extract it. Next, you just click the "PPSSPPSDL" file in the folder to run the emulator.

That's what his tutorial says. Here is angelxwind's website, since the PPSSPP site's Linux download section is broken. There are also instructions at the end of the page, read them carefully.

[URL="https://github.com/angelXwind/ppsspp"]https://github.com/angelXwind/ppsspp
[/URL]

Alternatively, if you cannot get it to install, Windows version works fine under WINE. You just run the exe and the program opens up.

---

### Post by brantpadams on 2013-07-16
I must be missing something and I can't tell if it's right in front of me or not. 

The only download I saw on the link you provided was for a .zip which is the master folder. Nowhere in it did I find the ppssppsdl file that I think runs it. I tried running the windows version under wine but I receive an error every time and I can't get it to open. So if the Linux pack exists, I simply don't know where to find it. I installed the SDL library easy enough as well as some other things in the instructions that I guess may or may not have been crucial. 

Is the Linux pack on his page? If so I simply don't see it.

---

### Post by Lightning Dragon on 2013-07-17
Hi,

I was afraid there would be missing files on the link I gave you. Did you try running the file in the folder? I think it is supposed to create it itself. I run the Windows version via WINE (I could help with that, too), but I'll see if I can find you a link with the file in it. 

And yes, it was on the homesite's download page, but the link is broken and is why I brought you a different link.

---

### Post by Lightning Dragon on 2013-07-17
Hi,

Alright, I can't find the file, but I did find two links that could prove useful for you.

[http://forums.ppsspp.org/showthread.php?tid=1298](http://forums.ppsspp.org/showthread.php?tid=1298)
[http://forums.ppsspp.org/showthread.php?tid=3291](http://forums.ppsspp.org/showthread.php?tid=3291)
[https://github.com/angelxwind/ppsspp](https://github.com/angelxwind/ppsspp)

I tried out the tutorial one, and I couldn't get cmake 2.8.8 or higher to install. All ways led to 2.8.7 which led to a sudo command error, but you might be able to do better than me in that regard. If not, you can always ask the people on the first link I gave you for some help.

---

### Post by brantpadams on 2013-07-17
I'm away from my home computer right now, but I'll definitely give those a shot when I get back. But for now, I wouldn't mine just getting the windows version to work under wine. It sounds like there's a simpler explanation for that one not working than the Linux build. All I get with the windows file is an error message that says it can't open. 

Thanks again for all your help.

---

### Post by brantpadams on 2013-07-17
So just to update you, I have a semi-working build going on Ubuntu thanks to a poster on the first link you sent me. It's version 7.6 and I can load a few games, but the graphics options are limited and the sound doesn't include music or it's not there at all. Crisis Core shows the first two logos and then a grey screen, but you can still access the start game options and pause option. 

I know the android version has a sound patch that fixed the music problem, but I don't know if the same patch is available here. I'd still like to see if it works better with the windows version under wine, but I'm happy to at least see I can get it working in some form.

---

### Post by Lightning Dragon on 2013-07-18
Hi,

If there are some problems and you are using the latest build, I would suggest checking out the [compatibility list]("http://forums.ppsspp.org/showthread.php?tid=1473") for the emulator or asking on their forum. According to the following link, CC is playable;

[http://forums.ppsspp.org/showthread.php?tid=1323](http://forums.ppsspp.org/showthread.php?tid=1323)

But apparently, you need to run off a save file to start CC.

---

### Post by Abhishek_Kalahal on 2014-06-22
Can you help me get PPSSPP running on Wine ? What are the dll's required? (Win version needed VC 2013 so..) Do you experience slow mo in the gameplay compared to linux? Thanks in advance for the help.

---

### Post by adec2 on 2014-06-22
To compile PPSSPP in Ubuntu (Check the PPSSPP web for package requirements before compile):

git clone git://github.com/hrydgard/ppsspp.git 
cd ppsspp
git submodule update -i
./b.sh
cd build
./PPSSPPSDL

Or copy PPSSPPSDL and the assets folder to your preferred folder and run

---

### Post by jahidul hamid on 2014-06-22
It may sound a little peculiar, but ppsspp runs better with wine than the native one. (at least the graphics is better)

---

### Post by jahidul hamid on 2014-06-22
you need wine and the windows version of ppsspp to get this working.

---

### Post by adec2 on 2014-06-23
It does sound peculiar because my experience of ppsspp is that it runs a lot better natively especially with all the graphical effects switched on. Sorry havent tried it with wine but i do know you should get music automatically in PPSSPP now if you compile it yourself and it is easy to do as my last post

---

