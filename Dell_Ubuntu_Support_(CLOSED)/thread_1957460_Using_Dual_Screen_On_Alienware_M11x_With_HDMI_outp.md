---
title: "Using Dual Screen On Alienware M11x With HDMI output (Geforce GT540M)"
date: 2012-04-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nuz25 on 2012-04-12
Hi, I am completely new to this forum and I need help to use a dual screen on my laptop. 

It's an AlienWare M11x R3 and I have a Samsung S24B350HL 24'' Screen. When I go to display it doesn't recognize the connected screen on my laptop. 

I didn't install any drivers directly as I don't really know how to get them. I guess I need a driver for my graphic card and/or for my screen. (I install Ubuntu updates thought)

I went in the additional drivers app, and it gives me no additional drivers available.

I hope someone can help me.

Thank you.

---

### Post by wane.dacha on 2012-07-12
Hey Nuz25,

I've got the same issue, same hardware (different monitor).  The problem comes from the NVIDIA Geforce card.  In the alienware M11x laptops, there's the underpowered graphics card on the cpu, and applications can be run using the Geforce (A GT 540m for me).  The switch on/off technology is known as Optimus, and it's really not supported well under ubuntu.  The closest project to bringing support right now is the Bumblebee Project (bumblebee-project.org). The Bumblebee project does a pretty good job of being able to switch the graphics card on and off for applications, but the issue is that it currently doesn't support.  They do, however, plan to add it in the future -- but who knows when that will be.

One of the things I've been trying to resolve is whether the HDMI comes from the intel card or the nvidia card with the hope that I can work that in-out.  From what I've looked up on the CPU graphics contained in my computer, a Intel Core i5 2467M @ 1.60GHz, it has the _potential_ to support hdmi in/out, but I can't find for sure if it's coming from the nvidia/intel.

Long story short, I have the same problem, but I think I can at least help with understanding what it is.

---

### Post by KaisaUbun2 on 2012-07-15
you have to Install bumblebee as of now this is your only option from there you can go back and install NVidia drivers.  Just open a terminal and type these seperate commands. 

```
 
sudo add-apt-repository ppa:bumblebee/stable 
sudo apt-get update 
sudo apt-get install bumblebee bumblebee-nvidia

```

---

