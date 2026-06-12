---
title: "Problem setting up left monitor as secondary"
date: 2013-12-07
forum: Desktop Environments
---

### Post by tseanschulze on 2013-12-07
Hello,

I am using the Xfce login on an Xubuntu 13.10 system.

I have a dual monitor setup with an Acer 22" monitor directly in front of me (DVI-0) and a Philips 22" monitor to my left (VGA-0). In order to get the panel and the desktop icons to remain on the Acer, I have had to set up Settings -> Display so that the system thinks the monitor on the left is on the right.  If I set it up so that the Philips monitor is on the left in Setting -> Display, then the panel and desktop icons shift all the way over to the left instead of remaining on the Acer monitor immediately in front of me. Visually, it's not really a problem having the system think the monitor on my left is on my right, but it is an annoyance having to move the mouse to the right to get it onto the monitor to my left.

How can I set this up so that I can have the panel and desktop icons on the center monitor and have the mouse move to the left to get to the monitor on the left?

Also, when I go into Settings -> Display, it shows the Acer monitor as "Acer Technologies 22"" but the Philips is shown as "Monitor." How can I get Settings -> Display to recognize the Philips monitor by name?

Regards,
Sean

---

### Post by heir4c on 2013-12-07
In SystemSettings>Display you have the option: Launcher placement. Can''t you change that?

---

### Post by tseanschulze on 2013-12-07
I don't see that option under Settings Manager -> Display.

---

### Post by heir4c on 2013-12-07
I'm sorry, I see now that you use Xubuntu and not Ubuntu with Unity.

---

### Post by tseanschulze on 2013-12-23
[COLOR=#000000]Hello,
[/COLOR]
I posted this in the absolute beginners section but did not get any responses that lead to a solution, so I've decided to repost my question here.

[COLOR=#000000]I am using the Xubuntu default login on an Xubuntu 13.10 system.[/COLOR]

[COLOR=#000000]I have a dual monitor setup with an Acer 22" monitor directly in front of me (DVI-0) and a Philips 22" monitor to my left (VGA-0). In order to get the panel and the desktop icons to remain on the Acer, I have had to set up Settings -> Display so that the system thinks the monitor on the left is on the right. If I set it up so that the Philips monitor is on the left in Setting -> Display, then the panel and desktop icons shift all the way over to the left instead of remaining on the Acer monitor immediately in front of me. Visually, it's not really a problem having the system think the monitor on my left is on my right, but it is an annoyance having to move the mouse to the right to get it onto the monitor to my left.[/COLOR]

[COLOR=#000000]How can I set this up so that I can have the panel and desktop icons on the center monitor and have the mouse move to the left to get to the monitor on the left?[/COLOR]

[COLOR=#000000]Also, when I go into Settings -> Display, it shows the Acer monitor as "Acer Technologies 22"" but the Philips is shown as "Monitor." How can I get Settings -> Display to recognize the Philips monitor by name?[/COLOR]

[COLOR=#000000]Regards,[/COLOR]
[COLOR=#000000]Sean[/COLOR]

---

### Post by e-San on 2013-12-23
Why do You care about it's name?

What graphic card do You use?

---

### Post by Iowan on 2013-12-23
Threads merged.
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not cross post, or post the same thing in multiple locations.
You may use the Report Post button to request to have the thread moved.

---

### Post by tseanschulze on 2013-12-24
Sorry, Iowan.  Clearly a failure on my part to RTFM.

e-San, the fact that it didn't show its name in Settings -> Display got me to wondering if it hadn't been recognized correctly, which I thought might be a factor contributing to the problem I'm having.

Using `lspci | grep VGA` shows the graphics card as: "Advanced Micro Devices, Inc. [AMD/ATI] RV770 LE [Radeon HD 4830]" I am not using the AMD/ATI proprietary drivers.  The card has VGA, DVI, and HDMI connectors. I am not using the HDMI connector with this setup.

Sean

---

