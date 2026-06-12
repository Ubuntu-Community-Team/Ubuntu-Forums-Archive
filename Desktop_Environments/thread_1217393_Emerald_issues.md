---
title: "Emerald issues"
date: 2009-07-19
forum: Desktop Environments
---

### Post by kjh_ngisd on 2009-07-19
Hi all,
Just replaced my laptop from a toshiba to a really spiffy HP. 
With some tweeking, Ubuntu is up and running, except for Emerald. 

It's all there (or seems to be) . I can select Emerald themes, but the themes just don't get applied. 
I've done some forum searching and tried a bunch of things that don't work. 
I've done emerald --replace, rebooted. I've rebooted. I've updated my video drivers. And tried a bunch of the other suggestions on the boards. But nothing -- no errors, just no themes. But it worked well on the Toshiba. 

I'm thinking it's the graphics card. But I'm not sure. 

Here's what I'm using:
HP DV7-2180 
ATI 4650 graphics card
1600 x 900 resolution (I think?) 
ubuntu 9.04 
gnome 2.26.1

Can anyone point me to something that may help?

thanks
--kevin

---

### Post by overdrank on 2009-07-19
Hi and emerald will need compiz. Are you able to use the visual effects, under system, preference, appearance, visual effects tab.

---

### Post by kjh_ngisd on 2009-07-22
> **overdrank said:**
> Hi and emerald will need compiz. Are you able to use the visual effects, under system, preference, appearance, visual effects tab.

Hi overdrank, 
thanks for the reply. 

compiz has been in. And I've been able to get to the visual effects tab on it. 
But when I change the Emerald theme, nothing happens. Even things like the emerald settings for what to do when with the right click on the menubar (for example) don't seem to have any effect. 

I did a quick scan of the mesg log, and there doesn't seem to be anything in there emerald related. 

As mentioned, I'd seen other threads on this, but nothing helpful. 
Most of them are outdated and talk about using beryl. 

--kevin

---

### Post by JK3mp on 2009-07-22
> **kjh_ngisd said:**
> Hi overdrank, 
thanks for the reply. 

compiz has been in. And I've been able to get to the visual effects tab on it. 
But when I change the Emerald theme, nothing happens. Even things like the emerald settings for what to do when with the right click on the menubar (for example) don't seem to have any effect. 

I did a quick scan of the mesg log, and there doesn't seem to be anything in there emerald related. 

As mentioned, I'd seen other threads on this, but nothing helpful. 
Most of them are outdated and talk about using beryl. 

--kevin

Are you applying it as your window manager? By default metacity is window manager in Gnome. Perhaps Ctrl+F2(to start run prompt) then type "emerald --replace", this will change your window manger from metacity to emerald, but you'll have to do this every time you login. 
-Peace

---

### Post by kjh_ngisd on 2009-07-24
yes. 
thanks JK3, but.. yes, tried that. 

I really do think it's something with the graphics drivers. Does anyone have the 4600-series card with Emerald?
--kevin

---

### Post by kjh_ngisd on 2009-07-26
> **kjh_ngisd said:**
> yes. 
thanks JK3, but.. yes, tried that. 

I really do think it's something with the graphics drivers. Does anyone have the 4600-series card with Emerald?
--kevin

I'm pretty sure it's the drivers, now. 
The last reboot, i completely lost the ability to enable advanced effects. No matter what I do, all I get is basic now, even though all I did was reboot. 
I go to the driver settings and they say everything is working ok, but clearly there's an issue. 
I'll check ATI's board. 
thanks for your thoughts.
--kevin

---

### Post by ~sHyLoCk~ on 2009-07-27
Better install fusion-icon and switch from there.

---

