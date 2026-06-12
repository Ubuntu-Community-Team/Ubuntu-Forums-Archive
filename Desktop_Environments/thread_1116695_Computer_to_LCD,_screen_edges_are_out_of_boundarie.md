---
title: "Computer to LCD, screen edges are out of boundaries"
date: 2009-04-05
forum: Desktop Environments
---

### Post by ofir_k on 2009-04-05
Hello,

I have a computer running Ubuntu 8.10, with nVidia GeForce 6600.

I am using DVI to HDMI cable to connect my computer to an LCD (DVI from the computer to HDMI on the TV).

The problem is that the screen edges are out of the LCD boundaries. Therefore, GNOME's menus cannot be seen (also scrollbars etc.).

The resolution of the screen is set to 1920x1080 (full HD). I have to mention that also when the resolution is 720p, the edges are missing, however, I can still see a little part of them.

Some screenshots are attached to illustrate the problem.

The red bounded area is the area which I can see. All other elements of the screen are hidden.

---

### Post by killshaman on 2009-04-06
> **ofir_k said:**
> Hello,

I have a computer running Ubuntu 8.10, with nVidia GeForce 6600.

I am using DVI to HDMI cable to connect my computer to an LCD (DVI from the computer to HDMI on the TV).

The problem is that the screen edges are out of the LCD boundaries. Therefore, GNOME's menus cannot be seen (also scrollbars etc.).

The resolution of the screen is set to 1920x1080 (full HD). I have to mention that also when the resolution is 720p, the edges are missing, however, I can still see a little part of them.

Some screenshots are attached to illustrate the problem.

The red bounded area is the area which I can see. All other elements of the screen are hidden.
I'm having the same issue with 1080p on a Philips 42" with an Intel G45 mobo and an HDMI cable out. The whole screen goes beyond what is visible and if I adjust the resolution, I end up with with black bars on every side. I want full 1080, so running at anything less would be against what I purchased the system for.

---

### Post by killshaman on 2009-04-07
I see a lot of the issues with the Intel x4500HD graphics card, which is what is on my motherboard. However, those issues usually relate to bad lines and the inability to have any connectivity at all. Mone has connectivity just fine, but the resolution settings are all weird. I set it to 1900x1080 and it works for a split second before expanding beyond the boundaries of my screen. Also, Ubuntu reports this as a 32" Philips when it's a 42" Philips. Any thought anyone? Anyone?

---

### Post by ofir_k on 2009-04-09
Do you think that it is not a bug related to the graphic card?

Maybe it is something related to X, or Gnome? Someone has tried 1080p on KUbuntu?

---

### Post by killshaman on 2009-04-09
I figure it out. My TV is set to auto-resize and it assumes the nav bars are not active picture artifacts or whatever. Works fine now. Tahnks for the help.

---

### Post by ofir_k on 2009-04-10
> **killshaman said:**
> I figure it out. My TV is set to auto-resize and it assumes the nav bars are not active picture artifacts or whatever. Works fine now. Tahnks for the help.

I didn't find any option in my TV saying auto-resize.

How is it named in your TV? and which model do you have? Do you connect your PC to your TV with an HDMI or DVI to HDMI cable? Which graphic card do you have?

I am asking all of this questions just to be sure what causes the problem.


Maybe it is something with X?

Help will be really appreciated!

---

