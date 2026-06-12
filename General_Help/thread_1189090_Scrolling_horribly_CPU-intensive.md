---
title: "Scrolling horribly CPU-intensive"
date: 2009-06-16
forum: General Help
---

### Post by unimatrix on 2009-06-16
System specs:
> 
CPU: AMD Athlon XP 3500+ 64
RAM: 2GB DDR
GPU: nVidia GeForce 6600
OS: Ubuntu 9.04 Jaunty Jackalope 64-bit (same on older versions)
Video drivers: nvidia 185 (latest, but problem is the same on older versions); dri2 & glx enabled
Compiz: OFF (turning it on slightly worsens the situation)
My xorg.conf: [link]("http://pastebin.ubuntu.com/197152/")


Demo video showing the horror of scrolling on Opera 10b2 (where it usually works best): [**link**]("http://files.getdropbox.com/u/121855/pub/16062009.mp4")
URL to website shown in video: [**link**]("http://www03.wolframalpha.com/input/?i=e%5E%28i%2API%2F4%29%2A+%28%28z%2B3%29%2F%28z-3%29%29")

Another video, this time showing [slashdot]("http://slashdot.org"): [**link**]("http://files.getdropbox.com/u/121855/pub/14062009%28003%29.mp4")


You can see in the video that even the music will stop playing, because all the processing power goes into scrolling.
Question number one is: is this supposed to happen? It doesn't happen on Windows...
Question number two: what can be done about it?

PS: Hope you liked the music.

---

### Post by DeMus on 2009-06-16
> **unimatrix said:**
> System specs:


Demo video showing the horror of scrolling on Opera 10b2 (where it works BEST!): [**link**]("http://files.getdropbox.com/u/121855/pub/16062009.mp4")
URL to website shown in video: [**link**]("http://www03.wolframalpha.com/input/?i=e%5E%28i%2API%2F4%29%2A+%28%28z%2B3%29%2F%28z-3%29%29")

Another video, this time showing slashdot.org: [**link**]("http://files.getdropbox.com/u/121855/pub/14062009%28003%29.mp4")
[Slashdot link]("http://slashdot.org")

You can see in the video that even the music will stop playing, because all the processing power goes into scrolling.
Question number one is: is this supposed to happen? It doesn't happen on Windows...
Question number two: what can be done about it?

Could you open a terminal and type
```
top
```
Then when you look at that, do the scrolling again. Then you can see which program or process is eating your CPU.

You write you installed the latest nVidia driver. Could it be something went wrong here and the CPU is doing all the GPU work?

---

### Post by Bachstelze on 2009-06-16
Did you install the correct drivers for your video card?

---

### Post by unimatrix on 2009-06-16
> **DeMus said:**
> Could you open a terminal and type
```
top
```
Then when you look at that, do the scrolling again. Then you can see which program or process is eating your CPU.


[IMG]http://img145.imageshack.us/img145/6850/screenshotterminalc.png[/IMG]
(the censored parts are obviously just my username)

> 
You write you installed the latest nVidia driver. Could it be something went wrong here and the CPU is doing all the GPU work?

Nope, I only did it because I thought it would help, but it made no difference.

---

### Post by DeMus on 2009-06-16
> **unimatrix said:**
> 

Nope, I only did it because I thought it would help, but it made no difference.

When I do the same, looking at top and scrolling a a Firefox page, the maximum percentage for Xorg is 13%. For you it is 88.8.
This is too much.
It could indicate the CPU is doing a lot of work which is normally done by the GPU. And that would indicate a not well installed driver.
Please type System- Administration-Hardware Drivers.
At the bottom of the screen, is the green light burning?

---

### Post by unimatrix on 2009-06-16
> **DeMus said:**
> When I do the same, looking at top and scrolling a a Firefox page, the maximum percentage for Xorg is 13%. For you it is 88.8.
This is too much.
It could indicate the CPU is doing a lot of work which is normally done by the GPU. And that would indicate a not well installed driver.
Please type System- Administration-Hardware Drivers.
At the bottom of the screen, is the green light burning?

The Hardware Drivers list is empty, because I installed my nvidia drivers from this repository: [https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/~thefirstm/+archive/ppa")

However, I can provide you with other information about the functionality of the drivers:
[glxinfo]("http://pastebin.ubuntu.com/197165/")
[glxgears]("http://pastebin.ubuntu.com/197169/")
[nVidia Settings]("http://img366.imageshack.us/img366/4561/screenshotnvidiaxserver.png")

EDIT: ["top" when scrolling the same webpage with Firefox]("http://img194.imageshack.us/img194/2614/screenshotterminalfiref.png")

---

### Post by DeMus on 2009-06-16
> **unimatrix said:**
> The Hardware Drivers list is empty, because I installed my nvidia drivers from this repository: [https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/~thefirstm/+archive/ppa")

However, I can provide you with other information about the functionality of the drivers:
[glxinfo]("http://pastebin.ubuntu.com/197165/")
[glxgears]("http://pastebin.ubuntu.com/197169/")
[nVidia Settings]("http://img366.imageshack.us/img366/4561/screenshotnvidiaxserver.png")

Strange. I installed the same driver, from the same site and look at my Hardware drivers-list.

glxinfo gave about the same info here, glxgears differs a factor 4 (but I have a 8500GT nVidia card so this could and should be faster) and the nVidia Settings are the same.
Why is Xorg eating so much CPU in your computer? I really don't know. Sorry.

---

### Post by unimatrix on 2009-06-16
You have to reboot the system for the kernel to load the newly installed modules if you have installed it from the PPA repository. You're still using Jaunty's default drivers.

---

### Post by DeMus on 2009-06-16
> **unimatrix said:**
> You have to reboot the system for the kernel to load the newly installed modules if you have installed it from the PPA repository. You're still using Jaunty's default drivers.

I did reboot since then. No idea why it still says 180 instead of 185. In the nVidia settings it is says 185.

---

### Post by unimatrix on 2009-06-16
> **DeMus said:**
> I did reboot since then. No idea why it still says 180 instead of 185. In the nVidia settings it is says 185.

Well, Ubuntu probably doesn't detect 3rd party drivers. But this is irrelevant anyway, because the drivers work.

Could it be that my CPU is simply too weak for Jaunty? It would be nice if someone with the same or similar processor could comment on this.

---

### Post by DeMus on 2009-06-16
> **unimatrix said:**
> Well, Ubuntu probably doesn't detect 3rd party drivers. But this is irrelevant anyway, because the drivers work.

Could it be that my CPU is simply too weak for Jaunty? It would be nice if someone with the same or similar processor could comment on this.

Well, if a AMD 3500+ is not capable of doing this then what is?
Since the Xorg is so high during scrolling I would say it is your 6600 nVidia card, but even this one should be capable enough.
I'm out of ideas, sorry. Hope somebody else will pick up this thread.
Good luck.

---

### Post by Vaphell on 2009-06-16
i'd blame drivers, i have gf6200 and it scrolls stuff just fine in my hardy heron
does compiz work for you?

---

### Post by unimatrix on 2009-06-16
> **Vaphell said:**
> i'd blame drivers, i have gf6200 and it scrolls stuff just fine in my hardy heron
does compiz work for you?

Yup it works. It drops the FPS on glxgears a bit, but otherwise it works alright.

---

