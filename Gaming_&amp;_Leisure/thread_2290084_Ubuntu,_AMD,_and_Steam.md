---
title: "Ubuntu, AMD, and Steam"
date: 2015-08-09
forum: Gaming &amp; Leisure
---

### Post by Mattaus on 2015-08-09
Hi all,

I'm sorry as this seems very familiar to a lot of topics, but I can't seem to answer the problem through searching. Well I know what the fix is, but it doesn't help with another problem...

I'm attempting to switch to Linux for as much of my day-to-day computing as possible. I play a lot of TF2 so I figured I could use Steam under Linux and TF2 should work fine.

Well first issue is I have an AMD card. I can't really help that at the moment though. I thought "how bad could it be" and was instantly worried when TF2 took forever to load compared to my old Windows install. Performance was then unplayable and super choppy. I did some Googling and people said the open source drivers were better than the propriety ones, so I reverted back to them. The problem with that is, Steam won't load with the open source drivers. It just give me this error:

> Running Steam on ubuntu 15.04 64-bit
STEAM_RUNTIME is enabled automatically
[2015-08-10 00:29:18] Startup - updater built Jul 23 2015 11:48:12
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)


Install propriety and it starts fine, but then TF2 is unplayable. Is it that bad that I should consider purchasing a Nvidia card? Will it improve that much, or should I just go back to Windows :(

I've done a fair bit of searching on how to improve AMD performance but none of it seems to really help. For what it's worth I'm running 15.04 with an i5-4590, Radeon 270X, and 16GB of RAM.

Any help or even just a pointer to some good information would be greatly appreciated.

Thanks.

---

### Post by R33D3M33R on 2015-08-09
Try these commands first: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

---

### Post by Mattaus on 2015-08-09
> **R33D3M33R said:**
> Try these commands first: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

OK, I gave that a quick try before I left for work this morning. It seemed to help but it is still kinda rubbish. I've done more reading (at work...naughty) and I have one question and few things I'll try tonight.

First up, when you install the fglrx proprietary drivers using the software GUI in Ubuntu, does that install the latest drivers available from AMD, or only what shipped with Ubuntu 15.04? 

I might try to install the Catalyst 15.7 drivers directly from AMD using the instructions noted [in this PDF]("http://www2.ati.com/drivers/amd-catalyst-graphics-driver-installer-notes-for-linux-operating-systems.pdf").

I've also seen it mentioned on more than one occasion that switching to xfce (or a similar light weight DE) helps with performance improvements as well.

Someone also mentioned turning vsync off. I can't recall if I had it on or not but it's on my list of things to mess with.

Thanks.

---

### Post by R33D3M33R on 2015-08-10
There will probably be no difference between Ubuntu and website version of Catalyst. DE should not have an impact for your computer, maybe vsync, but it's probably already off. 
You should verify if the opensource driver is correctly loaded by running the **glxinfo** command (you might need to install mesa-utils), paste the output here so it can be analyzed.

---

### Post by QIII on 2015-08-10
The version of fglrx in the repo for each release is frozen at the time of the release.  However, fglrx-updates *may* get updates.

The fglrx driver in 15.04 worked extremely well with my R9 290X during testing (see article in link to The Left Coast Geek) below.

Carry on ...

---

### Post by Mattaus on 2015-08-10
Hi guys, thanks for the replies. Extenuating circumstances have forced my hand somewhat so I've put this little project to bed for now. My plan is to build a new machine from scratch so will probably go with Nvidia hardware for that. My existing machine will remain on Windows. I will get a Headless Ghost HDMI dongle to mimic a monitor and use this on the Windows box to turn it into a headless steam server of sorts. Any games I cannot run under Ubuntu will be streamed over my household wired network to my Ubuntu box. Hopefully gaming performance with native Linux games will be improved with more appropriate hardware selection.

---

