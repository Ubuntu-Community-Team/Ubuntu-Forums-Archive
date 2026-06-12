---
title: "StarCraft Wine Problems"
date: 2007-05-31
forum: Gaming &amp; Leisure
---

### Post by Amyn on 2007-05-31
I have installed StarCraft under Wine, but I am having some issues.  The game does not take up the entire screen when I run it.  it completely crashes when I try to connect to Battle.net, and I am unable to patch it.

Thanks in advance,

Amyn

---

### Post by arsenic23 on 2007-05-31
I'm fairly sure you can get it to run full screen by entering winecfg into a terminal and messing with the settings there.   I'm fairly sure that if you don't have the virtual desktop enabled the alt+enter should make it fullscreen the same as in windows.

As for battle.net, I never did get that working myself.  But I'm fairly sure it's possible.  You'll have to search around or wait for someone else to post the solution.  Sorry I couldn't be of more help but I no longer have starcraft intsalled and it's been a while.

---

### Post by Amyn on 2007-06-01
Bump

---

### Post by odbod on 2007-06-05
Back in my dapper drake days, I was easily able to access battle.net. No problems, no screen issues, nothing. Everything was pretty much flawless.

---

### Post by Amyn on 2007-06-06
Welcome to the days of Feisty Fawn.  Doesn't solve my problem. 

I have downloaded and applied the patch, but Battle.net is a no go.

---

### Post by CaptainInsaneO on 2007-06-09
A solution for Battle.net can be found [here]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Starcraft").


I'm very interested in helping you solve your problem, because I had this same issue earlier today. Here's what I did to fix it:

Run winecfg as suggested.

Under the Applications tab, add StarCraft.exe to the list and make it compatible with Windows Version 98.

Under the Graphics tab, uncheck every box EXCEPT "Allow Pixel Shader..." and for Vertex Shader Support, select "None".

Click Apply, and try running StarCraft again. If you're still having problems, feel free to send me a private message so I can focus on getting you up and running.

---

### Post by Roadkill_ak_47 on 2007-06-09
hey i also am having the 1/4 screen issue, the application to win98 and graphix to unchecked and hardware at none. idea didnt seem to effect it

along with;
no audio (other then when the iso is launched) 
the games seems a bit laggy, is this normal or is somthin goin on?

---

### Post by CaptainInsaneO on 2007-06-09
Try rebooting your machine after making those changes and see if they stick. I forgot to add that in my last post. #-o they didn't work for me at first either, I rebooted and all was well.

As for your audio issues, see if you're using OSS as your driver. I've heard ALSA isn't too hot for StarCraft. If that doesn't solve it, look around on the forums and remember, Google is your friend.

As for the lagginess, I can't really speak for your machine because I don't know what hardware you're running, but start at your videocard.

---

### Post by jso2897 on 2007-06-10
I just installed it, and it plays great. No issues with the desktop after shutting down either, and it plays fine in fullscreen. On my machine (Yamaha Sound) the Alsa drivers work fine sound is good.
With all Windows games, setting the application emulation to the correct one is important. On my install of Wine, the default emulation was Win 2000 - and we all know Win2000 isn't exactly the gamers friend.

---

### Post by CaptainInsaneO on 2007-06-10
That's great that ALSA works good for you! I've heard a lot of people say they have problems with it, and I'm one of them. That's why I recommend OSS.

And you're right about the emulation, when I first started using Wine I took that emulation part for granted and later on realized it was probably the most important tool in winecfg.

---

