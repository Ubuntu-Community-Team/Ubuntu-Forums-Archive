---
title: "Screen Flashes With Compiz Fusion Turned on"
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by MONODA on 2008-03-27
I have compiz fusion enabled on a nvidia geforce 7400 go with 128 mb video memory(the rest of specs are in my sig) and after having it turned on for a while, the screen begins to flash for about 1/4 a second every few minutes. This usually happens while using a more than usual amount of cpu or ram. Restarting X fixes it but it comes back again later.

---

### Post by MONODA on 2008-03-27
I just realized that it seems the flashing part is moving from the top o my screen to the bottom and then repeating, sort of like it is falling down my screen. For example, first it will flash at the top, then at the middle, then at the bottom. note that there is a interval of about one minute between each flash.

---

### Post by MONODA on 2008-03-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/139196](https://bugs.launchpad.net/ubuntu/+bug/139196) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Another update, restarting X will not help. I have filed a bug report.

---

### Post by fizikz on 2008-05-10
Just to let you know, you're not the only one with this annoying problem. It happens to me too, and I'm still searching for a solution. If anyone has solved it, please let us know.


EDIT: Actually, in my case, it happens even when the cpu is not under intensive use. I haven't found a correlation between the flashes and anything else. However, it usually takes a while after boot-up for the flashes to start to occur.

Running Ubuntu 8.04 with compiz-fusion.

---

### Post by EXCiD3 on 2008-05-10
I have had issues sort of like this on HP dv9000t with an nvidia 7600go. My entire screen will flash completely black every hour or two and during spinning of the cube on compiz flickering that shows lines moving down the screen like described earlier in post #2. I realized that the flickering was just an issue with my video card's vertical syncing. Enabling Sync to VBlank fixed all the flickering issues when rotating the cube however the screen still blanks every hour or so for a split second.

---

### Post by fizikz on 2008-05-10
Thanks! I turned on Sync to VBlank using Nvidia's nvidia-settings control panel, under both X Server Settings and OpenGL Settings. It's too early to tell if the flashes are gone for good, but so far I haven't had any. I'm using an Asus laptop with an nvidia 7700go.

---

### Post by fizikz on 2008-05-17
Setting Sync to VBlank on seemed to get rid of the flashes for about a day, but they've reappeared now. I haven't been able to link the flashes to anything yet. If it makes a difference, I'm running compiz-fusion and cairo-dock. Also, these flashes seem random but they occur on the order of several dozen per hour. There can be a series of a few flashes within seconds of each other, then maybe a couple minutes of calm and then more flashes.

---

