---
title: "call of duty 1 with intel 915 won't start"
date: 2006-08-08
forum: Gaming &amp; Leisure
---

### Post by sitedesign on 2006-08-08
I have installed Dapper on a Dell 3100 which has an Intel 915 VGA on board. I installed Wine and used the Loki installer for COD.

The install went fine but the game won't start, it errors about the graphics card not supporting minimum features.

The game works fine under windows, so I guess the problem is with the driver used.

Has any one else got this working under Dapper with an Intel 915 card?

Any help appreciated.

---

### Post by bjweeks on 2006-08-08
You really should get a video card...

---

### Post by sitedesign on 2006-08-08
I would love to but this is just a workstation I use at work which is a Dell 3100, only has onboard VGA no AGP slot. Just a price thing.

---

### Post by WitchCraft on 2008-09-14
> **sitedesign said:**
> I have installed Dapper on a Dell 3100 which has an Intel 915 VGA on board. I installed Wine and used the Loki installer for COD.

The install went fine but the game won't start, it errors about the graphics card not supporting minimum features.

The game works fine under windows, so I guess the problem is with the driver used.

Has any one else got this working under Dapper with an Intel 915 card?

Any help appreciated.


You need to have OpenGL working.
What's the output of glxinfo | grep "direct"

If it is not direct rendering: yes, then you don't have OpenGL, and that's the problem.

Then you need to install libmesa etc.

---

