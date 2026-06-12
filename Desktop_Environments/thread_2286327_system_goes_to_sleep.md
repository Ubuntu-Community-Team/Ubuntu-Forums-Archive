---
title: "system goes to sleep"
date: 2015-07-11
forum: Desktop Environments
---

### Post by cmcanulty on 2015-07-11
I need this always on to access remotely. I have everything updated and all power manager things installed but still I can only set display at a max of 5 hrs and 50 min see screenshot all my other xubuntus allow it to go to never see screenshot

[ATTACH=CONFIG]263138[/ATTACH]

---

### Post by Dennis N on 2015-07-11
> **cmcanulty said:**
> I need this always on to access remotely. I have everything updated and all power manager things installed but still I can only set display at a max of 5 hrs and 50 min see screenshot all my other xubuntus allow it to go to never...

So, what version of Xubuntu are we talking about here?

---

### Post by cmcanulty on 2015-07-11
14.04 64bit

---

### Post by tgalati4 on 2015-07-11
You could set up Wake-on-LAN (WoL).  Many routers support port-triggering that sends a magic wake-up packet.  Then you have the entire delay-to-sleep period to log in.

---

### Post by Dennis N on 2015-07-11
> **cmcanulty said:**
> 14.04 64bit

The scale on mine goes from 'never' on the left, to '5hr 50min' on the right. Move the slider completely to the left. See image.

---

### Post by cmcanulty on 2015-07-11
I know it's supposed to work that way but on this computer it is greyed out and won't move even after completely removing and reinstalling the power manager.Now it has gone off again so I can't acccess it until the library opens again on Monday.

---

### Post by Dennis N on 2015-07-12
> **cmcanulty said:**
> I know it's supposed to work that way but on this computer it is greyed out and won't move even after completely removing and reinstalling the power manager.Now it has gone off again so I can't acccess it until the library opens again on Monday.

In that case, I would remove power manager from the "Application Autostart" tab in **Settings > Sessions and Startup** by un-checking the box. That will prevent it from shutting anything down.

---

### Post by cmcanulty on 2015-07-12
OK I will try that thanks

---

