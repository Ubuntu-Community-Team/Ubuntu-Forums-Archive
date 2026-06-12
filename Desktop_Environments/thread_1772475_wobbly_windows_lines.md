---
title: "wobbly windows lines"
date: 2011-05-31
forum: Desktop Environments
---

### Post by darude on 2011-05-31
I've just installed Kubuntu 11.04, switched on wobbly windows effect.
It runs very smooth on my Nvidia GeForce 7600 GS with dual screen twinview turned on.
However, I get these lines when I drag/move the window upwards - see screenshot:

Can anyone help resolve this minor annoyance?

[[IMG]http://img861.imageshack.us/img861/7230/wobbly.th.jpg[/IMG]](http://img861.imageshack.us/i/wobbly.jpg/)

[[IMG]http://img228.imageshack.us/img228/9769/wobbly2.th.jpg[/IMG]](http://img228.imageshack.us/i/wobbly2.jpg/)

---

### Post by wildmanne39 on 2011-05-31
> **darude said:**
> I've just installed Kubuntu 11.04, switched on wobbly windows effect.
It runs very smooth on my Nvidia GeForce 7600 GS with dual screen twinview turned on.
However, I get these lines when I drag/move the window upwards - see screenshot:

Can anyone help resolve this minor annoyance?

[[IMG]http://img861.imageshack.us/img861/7230/wobbly.th.jpg[/IMG]](http://img861.imageshack.us/i/wobbly.jpg/)

[[IMG]http://img228.imageshack.us/img228/9769/wobbly2.th.jpg[/IMG]](http://img228.imageshack.us/i/wobbly2.jpg/)
Hi, make sure you have sync to vblank in ccsm and nvidia manager disabled, and make sure the refresh rate is 60  in each of those also, the post back here and let us know if that fixed it.

---

### Post by darude on 2011-06-01
> **wildmanne39 said:**
> Hi, make sure you have sync to vblank in ccsm and nvidia manager disabled, and make sure the refresh rate is 60  in each of those also, the post back here and let us know if that fixed it.

I dont have ccsm installed.

I configured twinview through Nvidia X server settings (this was installed by default - perhaps by clicking third party during installation).

I'm using KDE's default - K Menu > System Settings > Desktop Effects > All Effects > Wobbly Windows

K Menu > System Settings > Desktop Effects > Advanced > Use VSync is checked

As for refresh rate, I turned on K Menu > System Settings > Desktop Effects > All Effects > Show FPS and it reports between 57 and 60 FPS during windows...wobblying!

[[IMG]http://img818.imageshack.us/img818/4636/vsync.th.png[/IMG]](http://img818.imageshack.us/i/vsync.png/)

---

### Post by wildmanne39 on 2011-06-01
> **darude said:**
> I dont have ccsm installed.

I configured twinview through Nvidia X server settings (this was installed by default - perhaps by clicking third party during installation).

I'm using KDE's default - K Menu > System Settings > Desktop Effects > All Effects > Wobbly Windows

K Menu > System Settings > Desktop Effects > Advanced > Use VSync is checked

As for refresh rate, I turned on K Menu > System Settings > Desktop Effects > All Effects > Show FPS and it reports between 57 and 60 FPS during windows...wobblying!

[[IMG]http://img818.imageshack.us/img818/4636/vsync.th.png[/IMG]](http://img818.imageshack.us/i/vsync.png/)
Hi, uncheck vsync.

---

### Post by darude on 2011-06-02
> **wildmanne39 said:**
> Hi, uncheck vsync.

Doesn't appear to make a difference unfortunately

---

### Post by wildmanne39 on 2011-06-02
> **darude said:**
> Doesn't appear to make a difference unfortunately

Hi, are you using the new nvidia driver 270, if so deacivate it and use the older one the new one has some issues and it does not work right with 11.04. I use the 173 and it works great, I do not know if that is the one you need but if is is listed in additional drivers activate it.

---

### Post by darude on 2011-06-03
> **wildmanne39 said:**
> Hi, are you using the new nvidia driver 270, if so deacivate it and use the older one the new one has some issues and it does not work right with 11.04. I use the 173 and it works great, I do not know if that is the one you need but if is is listed in additional drivers activate it.

Somethings do work better now that I switched to 173. I just realised this happens because I'm using a different window look and feel - I'm using Plastik. If I use the Oxygen look and feel instead, these lines doesn't appear.

Edit: actually if I use any other L&F (except Oxygen) these lines appear. So this bug appears in Tabstrip, Laptop, Plastik L&F.

---

