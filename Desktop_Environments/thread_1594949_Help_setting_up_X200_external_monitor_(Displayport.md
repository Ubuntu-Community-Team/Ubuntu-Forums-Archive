---
title: "Help setting up X200 external monitor (Displayport) resolution."
date: 2010-10-12
forum: Desktop Environments
---

### Post by anixon on 2010-10-12
I have finally decided to reach out for help because I've been messing around for 3 days with xorg.conf and I'm a beginner and not getting it right.

What I want to do is to use only my external monitor (1920x1200) via DisplayPort when my computer is docked. And then my laptop display (1280x800) when undocked. I am using Ubuntu 10.04.

I have setup System->Preference->Monitor: Unchecked <same image in all monitors>, turned off laptop display, and set External monitor to 1920x1200. After doing this everything works when in Xwindows. The resolution is correct when I am docked, and when I am undocked it defaults to my laptop display.

The ONLY problem with using the System->Preferences->Monitor is that when I start up the computer when docked the external monitor goes to the incorrect (laptop screen) resolution at the initial login screen. After I login the resolution corrects itself but it's messy with reinitialization of the screen and my icons being all messed up. I think this happens because these settings only take effect after logging in.

I believe I have to edit the xorg.conf to get my setup working at the login screen. Can someone please tell me how to this. Thank you.

---

### Post by anixon on 2010-10-18
anybody?

---

