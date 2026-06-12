---
title: "Random game lag, help is appreciated!"
date: 2009-03-02
forum: Gaming &amp; Leisure
---

### Post by DaveG825 on 2009-03-02
I posted this in multimedia and video, and no one responded, so I thought maybe you guys over here could help me. :P

> I hope this is the right place for this...

I finally got games such as OpenArena, Quake 3, and Warzone 2100 to run properly last night. There were a couple graphics problems, but after some time we realised that I just needed to switch all visual effects off. Anyway, everything worked finally and I was elated.

Unfortunately, this morning ALL games (not just fullscreen/opengl games) started lagging like crazy. The mouse, gameplay, sound, everything.

I think LinCity was working fine earlier. However, I plugged in my Rocketfish mouse in in preparation for OpenArena, and to make a long story short, I quickly realized that all of my games were lagging.

The only thing I could think of is that it has something to do with the mouse. It didn't prompt me to install any drivers, and I restarted the system once with the mouse plugged in and one without, and the problem still persists.

I'm running on a Compaq Presario with 1.5 gigs of RAM, an Intel 945GM integrated graphics card, and Ubuntu is the only OS on it.

Just an update:


Interestingly enough, Globulation2 runs fine. I just checked, all other games are still lagging like crazy.


EDIT: Screensavers lag too! It's gotta be some strange video problem. Oh, and I already checked my processes. Nothing outstanding. **[COLOR="Red"]NOTE: As you'll see below, processes DO show that most games take up the remaining 95% of my CPU, including small programs like Visual Boy.[/COLOR]**

---

### Post by R33D3M33R on 2009-03-04
Maybe the problem is hardware overheating. Did you check the temperatures?

---

### Post by grossaffe on 2009-03-04
perhaps having an intel graphics card could be your problem

---

### Post by DaveG825 on 2009-03-17
My hardware isn't overheating, that's one of the first things I checked.

Also, the Intel is integrated, so I don't really have a choice.

---

### Post by DaveG825 on 2009-03-17
Maybe my problem has its roots in compiz? I don't entirely understand compiz, but I do know that it has something to do with desktop effects... I think. As far as I've seen so far, my problem persists even with desktop effects on "none."

Thoughts?

---

### Post by Glucklich on 2009-03-18
> **DaveG825 said:**
> Maybe my problem has its roots in compiz? I don't entirely understand compiz, but I do know that it has something to do with desktop effects... I think. As far as I've seen so far, my problem persists even with desktop effects on "none."

Thoughts?

If the desktop effects are on "none", that ain't it.
Ubuntu ain't the best OS to play. I was never able to play Urban Terror on it more than 10 minutes. After those minutes, it plain crashed. And I enjoy that game very much.
If you're on a laptop (no matter how good it is), my advise is change to Xubuntu or any other "small-weight" OS as soon as possible. That is, if you notice that it is ventilating more than usual. I went too late on this one. But I guess that ain't the problem either, since you said it wasn't overheating.

---

### Post by DaveG825 on 2009-03-18
Thanks for all of the help so far, everyone. =]

I checked my processes, and saw that games are taking up what's left of my CPU! My computer was very powerful running Vista, and since everything was working fine up until two or so weeks ago, I doubt it's lack of ability on my machine. I quickly noticed that even Chromium (a simple side-scrolling shooter) starts taking up the remaining 95% of my CPU once I start it up.

OpenArena, Tremulus, Glest, Lincity, Visual Boy, etc. are affected by this problem.

Globulation 2, FreeCiv, and Gnometris and other simple games that were packaged with Ubuntu are not affected...

I hope somebody can pinpoint my problem, or at least give me a good direction to head in.

Also, as for Xbuntu, I might install that on some other partition. I was going to try Fedora, Slackware, and a couple other distros as well on separate partitions anyways.

---

### Post by hikaricore on 2009-03-18
It is the lack of power due to your Intel video chipset.
Your chipset likely has very crappy OpenGL support and heavy reliance on DirectX.

I'm sorry but it probably is due to lack of your machine's ability.
You can blame Intel for badly designing "video" hardware and barely bothering to write Linux drivers.

---

### Post by DaveG825 on 2009-03-18
So there's no workaround for this? Nothing besides getting a machine without a crappy integrated graphics card?

---

### Post by Glucklich on 2009-03-18
> **hikaricore said:**
> It is the lack of power due to your Intel video chipset.
Your chipset likely has very crappy OpenGL support and heavy reliance on DirectX.

I'm sorry but it probably is due to lack of your machine's ability.
You can blame Intel for badly designing "video" hardware and barely bothering to write Linux drivers.

That ain't it. I have a nVidia GeForce Go 7900 GS and I experienced the same things as he did. When the lag occurred (more like a freeze... I just sized the game window to confirm it), that the CPU was being 100% used. I only got OS stability when I installed Xubuntu. Maybe a even smaller OS would be better but I needed the computer working urgently and it did it.

Edit: Yeah, do that. Install it on another partition. You got nothing to loose. That did it for me, if it does it for you too... I'll be very happy. If it doesn't, hey... at least I gave my best shot. The way I see it, Linux needs to be as simple as possible. The more you have... the more likely it will get in your way.

---

### Post by DaveG825 on 2009-03-18
Thank you so much! I was beginning to loose hope. =D I'll try that right now. Besides, if it comes to it I can always try my luck on some other distros as well as Ubuntu. Thanks!

I'll report back with the results!

---

### Post by Glucklich on 2009-03-19
> **DaveG825 said:**
> I'll report back with the results!

Please do.

---

### Post by DaveG825 on 2009-03-19
Hey-- I'm trying to switch to Xubuntu. I've got the Xubuntu login screen, but when I reboot it seems to be starting up Ubuntu, and the only difference I'm seeing is there's some Xfce programs installed.

Besides switching the splash artwork with sudo, I've also done:

sudo apt-get install xubuntu-desktop
sudo apt-get remove xubuntu desktop
sudo apt-get autoremove

I'm not quite sure if that's right, but it seems to have worked in terminal. The only problem is that I'm still seeing GNOME and the ubuntu interface.

I obviously still want to be able to revert to Ubuntu later, in case the Xubuntu idea doesn't go so hot.

Thanks.

---

### Post by DaveG825 on 2009-03-20
Nevermind, I was able to get help with that elsewhere.

Still, it looks like the problem persists even in the xfce environment. I'm trying kubuntu as well, just for giggles.

Meanwhile, any other ideas?

---

### Post by Glucklich on 2009-03-22
> **DaveG825 said:**
> Nevermind, I was able to get help with that elsewhere.

Still, it looks like the problem persists even in the xfce environment. I'm trying kubuntu as well, just for giggles.

Meanwhile, any other ideas?

I'm sorry it didn't worked out for you. The only idea I can give you is Dual Boot. Solid and problem free XP gaming with friendly and solid Linux workspace. Plus keep in mind that if you only boot XP for gaming, it won't be filled with crap and will boot a lot faster. So, it's not a bad solution.

---

### Post by DaveG825 on 2009-03-23
I do have Windows XP Professional SP3 install disk, and I did try to dual boot. My problem is that when I wiped my hard disk, I apparently lost the required SATA/RAID drivers for my hard disk required for Windows to locate it. I don't have a floppy drive to put the drivers on during install, so I need to find a Windows machine somewhere where apparently I'm supposed to use a program called nLite to incorporate the necessary drivers into the Windows image...

Any easier way of accomplishing a Windows install would be wonderful.

Thanks again!

---

