---
title: "One Virtual Desktop Per Monitor/Using XRANDR"
date: 2010-03-14
forum: Desktop Environments
---

### Post by Lancelot59 on 2010-03-14
Before I start I'd like to say I did search around and didn't find anything useful that helped with this.

My problem: I have two monitors, my laptop screen, and an LCD monitor. I want to configure linux to put one virtual desktop on one, and a second on another. I'm using Compiz as well, so I'd like it to show one side of the cube on each monitor.

I'm not really sure how to go about setting this up though. My attempts so far have stretched the same desktop across both monitors, or resulted in an unusable monitor that just sits there with the default background.

While I was trying to figure this out I came across something called XRandR that lets you connect/disconnect monitors without restarting xserver. I'm not sure how to get this going either, the only tutorials I found were for intel chipsets, and I'm using the proprietary NVidia drivers.

---

### Post by dj3mb3 on 2010-03-22
Hi, Have you found any solution for that?

I'm also using nvidia proprietary driver, 
and I'm looking for that configuration.

I want to put virtual desktop 1 on monitor 1 (the main laptop one) and virtual desktop 2 on the 2nd connected monitor

But no idea about getting it

thanks

dj3mb3

---

### Post by RED666 on 2010-03-22
I don't think this possible, not that I would know...I'm also just starting out on Ubuntu. But it doesn't seem logical, the virtual screens ( you mean workspaces right?) are VIRTUAL, lol. Each  workspace represents all your attached displays together.

That's what I think for what it's worth

---

### Post by Lancelot59 on 2010-03-22
> **dj3mb3 said:**
> Hi, Have you found any solution for that?

I'm also using nvidia proprietary driver, 
and I'm looking for that configuration.

I want to put virtual desktop 1 on monitor 1 (the main laptop one) and virtual desktop 2 on the 2nd connected monitor

But no idea about getting it

thanks

dj3mb3
Not yet no. I've managed to get a seperate XScreen running, but that just showed the blank background and trapped my mouse when I moved there. I think this feature needs to actually be worked into Ubuntu. Currently it doesn't seem possible.

---

### Post by asmoore82 on 2010-03-22
You have to create new panels and drag them over to the 2nd monitor.

---

### Post by Lancelot59 on 2010-03-22
Eh? I don't understand. I want one viewport per screen, so how would I go about configuring that?

---

### Post by Nandox7 on 2010-03-23
Hi,

The proprietary Nvidia drivers provide "Twinview" or "Separate Displays".
What Twinview allows is like Xinerama, is a "virtual" mode that combines the size of the 2 displays and to the X server it sees it as one.
It has some drawbacks, like the wallpaper is stretched over the total area, or if one display has bigger resolution than the other a null "gap" is created.

Separate Displays allows you to have two displays showing two different workspaces, but without the option to move applications from one to the other.

So what you want AFAIK is not possible, having two workspaces that can share applications and each one visible in a different display.
A workaround for this can be adding a second panel to the second display and fill it with the same applets as the main one, launchers and task list.

Hope this helps.
Oh, and use the Nvidia settings tool to make the changes.

---

### Post by Lancelot59 on 2010-03-23
So how do I make that second panel?

---

### Post by asmoore82 on 2010-03-23
right-click a vacant spot on an existing panel and pick "New Panel"

---

### Post by Lancelot59 on 2010-03-23
How do I do that when the second screen eats my mouse?

---

### Post by nosarembo on 2010-04-05
I have never seen this done with virtual desktops.

*But* you *can* have one big desktop that spans both monitors, using xrandr. That will give you most of the benefits of two virtual desktops.

So you can eg have your email on the left screen and an IDE on the right screen.

---

### Post by Lancelot59 on 2010-04-05
I guess that works. :/

---

### Post by e.m.fields on 2010-10-15
This is possible. I do not know how to do it, but the "this is not possible" responses are incorrect.  I'm researching this now ... obviously, it's just icing, but I think that it's a pretty useful thing if you can get it going.

We're looking into something called nvidia "twinview" and / or "multihead" display.  I've seen a lot of talk about "xinerama", but I'm not sure if this is a necessary component here, and I gather it's a deprecated solution.

There's promising leads I've seen talking about getting the rigiht xorg.conf configuration.

We shall see.  
If anyone gets an answer, please be sure to post it here and mark as solved!

---

### Post by Lancelot59 on 2010-10-15
Do you work with the XServ team?

---

