---
title: "chat with cam"
date: 2009-04-22
forum: General Help
---

### Post by rastro123 on 2009-04-22
Hi folks,
Could anyone pls tell me if they have actually managed to get video chat working in intrepid, and if so, how they did it? I've tried amsn, I can see her, but my bird can't see me. Ekiga does absolutely nothing. In Kopete, I click the cam button and again absolutely nothing. (Im using a library- says Im behind a firewall, however there is no problem with windows using messenger) I'm looking for some fairly basic go here and and do this intructions. I love this linux stuff, and Im so glad I bought a new pc with vista on it, cos it pissed me off so much, I discovered linux. I should send them a thankyou note. But.....Im going crazy, not being able to talk to my bird without a cam. I tried to install windows 7, so I could set up dual boot and use yahoo mess when I need to, but it won't have it, saying it needs ntfs. Any help most welcome, thanks.

---

### Post by deadned on 2009-04-22
I've wondered about chatting with the cam too. 

do you know what kind of camera you have? Have you gotten any other programs to recognize your webcam?

---

### Post by Claus7 on 2009-04-22
Hello,

the best program in order to be able to have both audio and video conversation at the moment, according to my experience, is skype even from dapper release.

Amsn is doubtful whether it will work with intrepid or not. The camera should be recognised, yet the farsight dependency libraries that intrepid has are not the ones required. 

In dapper I was able to have camera enabled in amsn and it was working nicely. In jaunty, which is supposed to have all the necessary dependencies for amsn to work, the camera was not tallying with that of dapper and the audio conversation refused to work. (That is according to my experience in the release candidate of jaunty).
Installing amsn from launchpad though in jaunty you can have easily installed many plugins and skins with one click away.

So go for skype at the moment. And if you stick to intrepid, I would advice you to forget amsn for audio and video conversation unless you compile a lot of libraries for yourself.

All of these presupose the fact that your camera is recognised in general by your system.

Regards!

---

### Post by meeples on 2009-04-22
hmm I've used aMsn, since Hardy on both my systems and ive never had a problem with video or audio chat.

:confused:

---

### Post by Claus7 on 2009-04-22
Hello,

> **meeples said:**
> hmm I've used aMsn, since Hardy on both my systems and ive never had a problem with video or audio chat.

It's nice that you report that. Up to now I was not able to have both audio and video conversation in amsn. Just video. How did you install amsn? Are you able to configure the contrast in your camera? Every time I try to make a conversation it drops and the system freezes for a small amount of time. That's in jaunty. Are your conversations with ubuntu or windows?

Regards!

---

### Post by rastro123 on 2009-04-22
apparently my cam is hp v412. When I go to the configuration settings it see it ok, but nothing gets transmitted.

---

### Post by norm.h on 2009-04-22
Have a look at this thread
[http://ubuntuforums.org/showthread.php?t=593231](http://ubuntuforums.org/showthread.php?t=593231)

norm

---

### Post by meeples on 2009-04-22
> **Claus7 said:**
> Hello,



It's nice that you report that. Up to now I was not able to have both audio and video conversation in amsn. Just video. How did you install amsn? Are you able to configure the contrast in your camera? Every time I try to make a conversation it drops and the system freezes for a small amount of time. That's in jaunty. Are your conversations with ubuntu or windows?

Regards!

wait no. im confusing myself. ywea i can change contrast and stuff and webcam works but i havent tried audio,:lolflag: i dunno why i typed audio :confused:

sorry if ive confused you,  confused myself abit. :roll:

---

### Post by Claus7 on 2009-04-22
Hello,

> **rastro123 said:**
> apparently my cam is hp v412. When I go to the configuration settings it see it ok, but nothing gets transmitted.

I do not think that a firewall will cause you problems, yet maybe a rooter. Have you tried to see whether the ports that the program you are using are forwarded or not?
I'm still thinking that the best program you can try is skype, yet it's your choice.

> **meeples said:**
> wait no... 

No problem at all. I just was wondering what you had done.

Regards!

---

### Post by rastro123 on 2009-04-23
hello mate, I had a look at the page, and when I look in the system log, I see refereces to the cam, that...er, looks ok, I think. But then I took a look using luvcwiew program, and this is what it says:
SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
  Frame size:   640x480
  Frame rate:   24/1 fps (requested frame rate 30 fps is not supported by device)

as you see frame format and rate, says not supported, - what do you think, can this be what my probs are, and is there anything I can do to resolve it? Cheers.

---

### Post by Claus7 on 2009-04-27
Hello,

I suppose that the camera is a usb one. So type lsusb in order to see how it is recognized. Now, the specs you give are nice, yet I have no idea which program you used. 

-From jaunty in synaptic I cannot find such a program and I cannot find that command either. The not supported thing is bad-

Till I saw that it was luvc**v**iew!

Ok, no I do not think that this is your problem. Have you tried skype? Have you tried to configure your camera via amsn's configuration panel? There it is supposed to "see" your surroundings and be configured accordingly. If you cannot see "yourself" there, then I do not think that someone will be able to see you.

Regards!

---

