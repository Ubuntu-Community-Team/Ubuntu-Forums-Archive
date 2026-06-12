---
title: "Audio Problems when Gaming in Steam und Ubuntu 22.10"
date: 2023-05-13
forum: Gaming &amp; Leisure
---

### Post by Illoran on 2023-05-13
Hi all,

i've encountered serious audio issues during gaming under Ubuntu 22.10. The sound is crackling, glitching out or is lagging behind and played real slow. This usually happens in Games where a lot of audio is layered on top of each other like Borderlands, The Riftbreaker, Dyson Sphere Programm and so on. First i suspected it was a performance issue, however the glitches don't seem to be correlated with FPS drops, and occur even at totally stable high framerates and decent cpu and gpu usage.

I've searched around for possible solutions, but sadly most attempted fixes i can find online are written for pulse audio and not pipewire. The few Pipewirehacks out there concerning default values in /etc/pipewire/pipewire.conf didn't fix the issue. 

Anyone got any idea what i can try ... help would be much appreciated :)

Best regards
Illoran

PS: My Audio setup is a Scarlett 2i2 interface connected via usb not the motherboard audio out ... if that's any help.

---

### Post by TheFu on 2023-05-14
Support for Ubuntu 22.10 ends in June. You have about 6 weeks to move to 23.04, which will be supported until January 2024, so you must move to 23.10 when it is released.  The good news is that 24.04 is about a year away and will be an LTS with at least 3 yrs of support for most DE variants or 5 yrs for the main, stock, gnome-based desktop.

In short, it isn't worth the effort to try fixing anything on 22.10 anymore.  Nobody is working on that release.  That's the main reason most people are better off running only LTS releases.

Are you using a low-latency kernel?  That seems to be step one.  I know next to nothing about pipewire.  None of my systems use it, at least not that I've noticed.

---

### Post by mofof on 2023-05-27
Hi, I also think we have to wait for version 23.04

[RIGHT][SIZE=1][URL="https://tweakbox.mobi/"][COLOR=#a9a9a9]


TweakBox[/COLOR][/URL] [[COLOR=#a9a9a9]Tutuapp[/COLOR]]("https://tutuappx.com/")[/SIZE][/RIGHT]

---

### Post by TheFu on 2023-05-27
> **mofof said:**
> Hi, I also think we have to wait for version 23.04

That happened last month - April. Get it or a flavor of your choice here: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
[https://www.howtogeek.com/883728/whats-new-in-ubuntu-23-04-lunar-lobster/](https://www.howtogeek.com/883728/whats-new-in-ubuntu-23-04-lunar-lobster/)
Be sure to read the release notes BEFORE anything else. [https://discourse.ubuntu.com/t/lunar-lobster-release-notes/31910](https://discourse.ubuntu.com/t/lunar-lobster-release-notes/31910)

Life is much easier if we stick with LTS releases only, which get 3-5 yrs of standard support, not just 9 months.

---

### Post by beirute2 on 2023-09-03
> **Illoran said:**
> I've searched around for possible solutions, but sadly most attempted fixes i can find online are written for pulse audio and not pipewire. The few Pipewirehacks out there concerning default values in /etc/pipewire/pipewire.conf didn't fix the issue.

I suffered with this for a long time until I was suggested to delete Speech Dispatcher. It worked perfectly for me and today I always do this with the computer of someone who has hearing problems.


Use this command in Terminal and restart your computer:


```
sudo apt-get remove --purge speech-dispatcher*
```

PS: My system is Ubuntu 22.04

---

### Post by #&amp;thj^% on 2023-09-03
> **beirute2 said:**
> I suffered with this for a long time until I was suggested to delete Speech Dispatcher. It worked perfectly for me and today I always do this with the computer of someone who has hearing problems.


Use this command in Terminal and restart your computer:


```
sudo apt-get remove --purge speech-dispatcher*
```

PS: My system is Ubuntu 22.04
I just replied on your other thread found here:[https://ubuntuforums.org/showthread.php?t=2490403&p=14156644#post14156644](https://ubuntuforums.org/showthread.php?t=2490403&p=14156644#post14156644)
Could you share those links you mention, I'm just very very curious how this helped?

---

### Post by beirute2 on 2023-09-03
@1fallen

Your are right, i suggested the same solution because I really use it lol
I am going to find the discussion i read about it, when I find it I'&#314;l send or contact you!
I am noob, I even don´t know what's this *thing *:P

---

### Post by #&amp;thj^% on 2023-09-03
That would be great, and you can just paste them here is good. :)

---

