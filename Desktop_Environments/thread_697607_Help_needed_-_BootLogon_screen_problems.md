---
title: "Help needed - Boot/Logon screen problems"
date: 2008-02-15
forum: Desktop Environments
---

### Post by molemoore on 2008-02-15
Hello,

This is my official first post here. I just took the leap and put Ubuntu on my Tablet PC to get rid of Vista (still have dual boot "just in case"). That was a tough switch cause I had to give up the tablet part of my computer, but here I am anyways. Anywho, to my issue...

I installed Ubuntu (7.10 I believe) a few weeks back and it has been working great. Everything has been working great, I have been really pleased. That is, at least until a couple nights ago. Basically, I was using my PC, everything going fine, and I shut down for the night. The next morning I started my PC again and it will not boot. A couple things I noticed: First, I now see some commands on the screen, before it was just the Ubuntu loading logo. Second, the last line that says "OK" on it, and the last line on the screen is:

* Running local boot scripts (/etc/rc.local) [OK]

The command prompt just sets there...blinking...taunting me...staring me down so to speak.

Note: I do see the Ubuntu loading screen before the command lines. The progress bar finishes and then the command lines show up. I would say that that is the point where the login screen usually is displayed.

Anyways, the only thing I did the prior night that was out of my norm was I played with the display settings a little, I tried to hook up a second monitor and use the two of them but I could never get it to work so I gave up and change everything back to its original setting (or so I believe I did) and all was well. Other than that I was browsing the web, nothing special. I played with Eclipse a little, but did no coding and listened to some music.

My experience level: Pretty much none. I am an IT pro but I am pretty much new to linux, so step by step would be nice to start with. I have begun reading n00b stuff to get up to speed but I am not there yet.

As always, any help is appreciated. Please let me know what additional information you need.

Thanks!

mole

---

### Post by ad_267 on 2008-02-15
If it was changing graphics settings that caused the problem you could try booting into recovery mode and running this command to reset your video settings to default:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That means you'll have to reset your video settings and re-enable proprietary drivers once you get things working again.

What video card and driver are you using? I found that the screens and graphics tool didn't work well at all with my displays and I managed to get dual displays working using the nvidia-settings tool that comes with the nvidia drivers. There are a few guides around for settings up dual monitors if you have a search, I think it's one of the trickier things to get working properly.

---

