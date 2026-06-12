---
title: "Dell Mini 9 tons of problems"
date: 2011-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TonyTheBean on 2011-08-30
Okay, so here's my story.
About a year ago i dug up my Dell Mini 9 and tried to install Ubuntu 10.04 through wubi, which screwed over the SSD somehow, thus making me run it off the Live CD (through USB flash drive) when i wanted to use it. Now, about a week ago my main computer crapped out, and i cant afford the required parts right now, so i'm stuck with the mini 9 for a while. So i installed 10.04 netbook remix to my flash drive and ran it off there for a while, but i was having a ton of problems with the background menu when i plugged in my TV with a vga cable to the laptop. Sometimes the menu would just go away and never come back without a restart, sometimes it would run like my monitor res was at 640x800. Then i decided to install 11.04 on my external hard drive and work off that, which went well and is running better then that 10.04 netbook remix i installed.

So here are my problem's. I just plugged in my external monitor and its restricting it to 1024x768, which it didn't do on 10.04. What 10.04 did do was restrict it to 1368x784 or something along that, which gave me these borders on the sides of my screen. I have tried putting stuff in the xorg.conf that was suppose to change the res to 1280x720 but didn't work. Now, my second problem.

Everything runs SLOW. I cant have music playing and chromium running at the same time, or everything is slow as hell. I also cant run firefox, or my computer just freezes after a bit of browsing. Skype freezes alot during calls if i have anything else running. This was also happening in 10.04, just worse.

Third problem!
I have a Saitech Cyborg R.A.T.7 mouse which does work for a minute or so, then after that minute i cant click anything.

Okay, i think that's about it. I'm not asking one person to answer every question (but if one person does, tons of cookies for them).

---

### Post by snowpine on 2011-08-30
Welcome to the forums!

I am an experienced Mini 9 owner so I will try to answer your questions as best I can. Unfortunately I am not familiar with your brand of external monitor or mouse. But I can try to help you figure out why things are running slowly.

A good first step is to run the System Monitor and figure out where the bottlneck is. Is your CPU near 100%? Is your RAM usage near 100%? Is your hard drive full? Which application or applications are consuming the majority of your system resources?

---

### Post by TonyTheBean on 2011-08-30
Right now I'm installing some stuff via terminal, i'll post a screenshot of the system monitor screen in about 15 minutes.
**Edited:** From what i remember, it idles around 75% on core 1 and around 95% on core 2.

---

### Post by TonyTheBean on 2011-08-30
During Install:
[IMG]http://i.imgur.com/r0yW6.png[/IMG]
After Install:
[IMG]http://i.imgur.com/dpz4h.png[/IMG]

Guess i was wrong about the idling %.

---

### Post by snowpine on 2011-08-30
Well, the Atom is a very low-end processor, so it is normal for it to spike to 100% when you are doing intensive activity like unpacking compressed software packages. 

I just checked and my Dell Mini 9 idles around 30% CPU. However, that is using a non-Ubuntu distro with a very lightweight windows manager.  

My recommendations are:

1. Install Ubuntu to your internal SSD drive. This will be faster for any task involving disk access compared with a USB drive

2. Try a lightweight desktop environment/windows manager such as LXDE, Fluxbox, etc. instead of Unity. These can be easily installed from the Software Center and then selected from the login screen.

---

### Post by TonyTheBean on 2011-08-30
Okay, well what about my monitor problem?

---

### Post by snowpine on 2011-08-30
No idea about the monitor problem. Perhaps another forum member can better assist? 

Have you tried pressing Fn+8 to switch monitor modes?

---

### Post by TonyTheBean on 2011-08-30
All that did was change my theme :confused:

---

