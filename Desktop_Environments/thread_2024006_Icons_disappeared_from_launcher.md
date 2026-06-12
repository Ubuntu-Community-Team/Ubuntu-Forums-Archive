---
title: "Icons disappeared from launcher"
date: 2012-07-13
forum: Desktop Environments
---

### Post by Acharn on 2012-07-13
So this morning I was browsing my regular blogs and news sites, and I noticed the Update Manager sitting in the launcher. I clicked on it, it said there were 52 updates ready, and so I went ahead and clicked on the "install" button. I've been so confident of Ubuntu upgrades that I didn't pay much attention to what was being installed, but I remember sometning about the OpenGL Library and Linux Extras 3.5.0-4. I had to run the manager a couple of times to get all the files downloaded, which is normal, and then it announced that I needed to restart my computer to finish the update. OK, I was at a convenient stopping place and clicked on "Restart now." When everything finished loading my Compiz Unity desktop looked normal except for tha launcher. What I have now is a gray, 50% transparent bar running along the left side of my screen. The icons are not visible, but thank goodness the tootips show when I move the cursor over them, so I can still operate. I have my choice of other desktops, and I suppose I could learn to love Gnome 3, but I've only ever tried out the others and immediately gone back to Unity, which I've really come to like.

Trying to remember what I've changed, a likely suspect came to mind. Last month I installed a theme/customization called Ambience Chameleon, which changes the background color of the launcher to match the desktop wallpaper. I have an ATI Raydeon x1550 (R515) graphics card running with the open source drivers, and that may be connected. Any suggestions?

---

### Post by lolpenguin on 2012-07-13
Screenshot?

---

### Post by Acharn on 2012-07-14
> **lolpenguin said:**
> Screenshot?

Attached. The darker rectangle along the left side is where the launcher is. When I move the cursor over it, I get the tooltips thowing the name of the program whose icon is supposed to be there, and I can run the program by clicking, just as usual. The small white dots are the indicators that the program is running and whether background or foreground.

I've tried changing themes and changing icon sets, but no effect.

---

### Post by gschoper on 2012-07-14
I had te same thing happen after applying updates yesterday and after a second reboot everything was fine.

---

### Post by Acharn on 2012-07-14
Well, I've rebooted several times and still have the problem. It's an annoyance, not crippling, and I could always try one of the other desktops. Gnome 3 is OK, IIRC. I don't care much for Cinnamon because of my love/hate feelings toward M$. I was kind of intrigued by the article at webupd8 (I think it was) about making the desktop look like the Mac Lion, and maybe I'll try that for a while. Meanwhile, I'll hold off aa few days before I mark the thread [Solved].

---

### Post by colorprint on 2012-07-15
I have the same problem for the all last week.
Reboots and unity reset not fixed it

---

### Post by Acharn on 2012-07-15
> **colorprint said:**
> I have the same problem for the all last week.
Reboots and unity reset not fixed it

Yeah, I should have mentioned I tried "unity --reset" as well. Got a bunch of error messages and had to reboot, but still have the problem. One thing I haven't tried yet is using a different desktop for a while and then booting in to Unity again. I should do that.

Out of curiosity, what kind of graphics card do you have? I have ATI Raydeon x1550, and I'm pretty suspicious of it. I have problems with the graphics in some Windows games run in Wine, even though the Wine Appsdb lists them as gold or platinum. Mostly I don't mind any more, but it would be nice to figure out what that's about.

---

### Post by Acharn on 2012-08-17
Well, patience paid off. Had another update today. Took eight or ten tries to get everything downloaded. I have lots of problems with my DNS. After trying to download from four different servers finally gound one that worked. Download complete, have to reboot. Click OK and voila! Suddenly icons appear on my launcher again. Don't know which one it was, there were a bunch of xorg and libgl stuff, but I noticed one title included "radeon," my graphics card, so maybe that was the one. So I'll mark this thread "solved."

---

### Post by Alexis Wilke on 2013-01-14
I've got the same problem. I also suspect that an update is the culprit although the icons went poof! while I was working on the computer. I did not pay too much attention to it as often restarting X windows is enough. But in this case, it looks like it may be pretty permanent. At least until I get the magical upgrade that makes it all appear again. I'll have to reboot, but am on a server that cannot be stopped too much during the day.

I already got some new updates and hope that will include the necessary fix for that glitch!

---

