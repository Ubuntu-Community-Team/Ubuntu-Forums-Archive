---
title: "Windowing Issue - Cant Click Some Parts Of The Window"
date: 2024-05-22
forum: Desktop Environments
---

### Post by kinderfeld on 2024-05-22
Hey All, I am having a very strange windowing issue that just started a few days ago. At first I thought it was just WINE apps, but then I noticed Discord was having the same issue today.

Basically here is what is happening. When a program is ran and than Maximized to full screen, only like 2/3rds of the top left of the window I am able to click on, the other right and lower bottom section of the window, when you click it, it just goes straight through to the desktop. So essentially only what the program originally popped up as I am able to interact with. So if say the window loaded up at 1600x900 pixels and I then maximized it to 1920x1080 pixels or larger. I can only interact with 1600x900 pixels of that window.

My System: Ubuntu 24.04LTS - GNOME - Wayland 

Any ideas on what has happened or how I can fix this?

**EDIT:** Come to think of it, this all started when I was playing around with the Desktop Fractional Scaling.

---

### Post by coffeecat on 2024-05-22
Support, not chat. *Thread moved to **Desktop Environments**.*

---

### Post by kinderfeld on 2024-05-23
OK I have identified the issue and seem to have fixed it. 

It has to do with Fractional Scaling. 

When I was playing around with Fractional Scaling, I had set the scaling back to 100% before turning off FS. 
To fix the issue I had to turn FS back on, set scaling to 150%, then turn it off again. This time without setting the scaling back to 100%.
Which for some reason, despite defaulting back to 100% anyway, it is now fixed. 

So this is most likely a bug with how the scaling settings is being written back to the settings file it uses. At least that is my assumption without bothering to dig any deeper. 

Note, this seems to only affect non GTK4 apps. Like Discord and programs running in Wine or Java based stuff. 

Anyhow, hope this helps for anyone else that runs into the issue.

---

