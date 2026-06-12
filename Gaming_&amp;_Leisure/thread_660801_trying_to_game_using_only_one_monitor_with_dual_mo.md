---
title: "trying to game using only one monitor with dual monitor setup"
date: 2008-01-07
forum: Gaming &amp; Leisure
---

### Post by tim018 on 2008-01-07
ok, so i just re did my computer setup, i now have dual monitors, which works great in ubuntu.  everything works great except one thing, gaming.  whenever i open a game it stretches between both screens.  how do i make it only use one screen for gaming and two for standard usage?  any help would be appreciated, thanks

also, let me know if you need any other info about my comp

---

### Post by Thundercat on 2008-01-12
Hi, I'm having the same issue.
I was thinking of making 2 seperate xorg.conf files ie xorg.conf.single and xorg.conf.dual and making some kind of script that would copy the one I want to use the xorg.conf and then reload X

I'm a linux newbie though so I'm not exactly sure if that would work or how well? If any experienced users could offer advice that would be great :D

---

### Post by wishyjr on 2008-01-12
i'd recommend running any games in windowed mode and trying out different resolutions to try and fill a single screen as best you can - its  a it of a sacrifice if you love to play full screen but ive learn't to live with it and im actually quite happy gaming with one screen.

---

### Post by DarwinsTheory on 2008-01-12
If your running an nvidia card then in theory its real easy...!

In your Screen section add  (Of course change for the resolutions etc you need)
Option "metamodes" "CRT: 1680x1050 +0+0, DFP: nvidia-auto-select +1680+0; Null, DFP: 1680x1050; Null, DFP: 1280x1024; Null, DFP: 1024x768"

To get more info just google "metamodes"

What this does is when you select 1680x1050 it turns off one of the monitors...!   Now for some reason it worked for me for awhile then all of a sudden stopped... I dicked with it for a few hours and gave in.. 

Now I just use the nvidia settings tool and switch off one screen before loading a game.   The downfall is that my task bar moves over and when i go back to dual screens I have to manually move it over again.

The command to launch the settings tool is nvidia-settings assuming you have it installed etc.

Anyhoo, manual but as I have to switch off Compiz I'm ok with it.

Matt

---

