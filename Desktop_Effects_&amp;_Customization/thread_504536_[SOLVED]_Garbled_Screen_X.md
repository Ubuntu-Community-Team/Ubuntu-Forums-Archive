---
title: "[SOLVED] Garbled Screen :X"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by Jonq on 2007-07-19
Hi,

After trying to install my gfx cards driver(8.38.7)for my Ati mobility x700, my login screen got garbled. its like 2 login sessions are on top of each other one working and one garbled after switching to tty and back to X makes them separate and i get non garbled version of the login while the garbled one running either F8 or F9.


and it does look exactly like this [http://i67.photobucket.com/albums/h283/SwordRaven/Screenshot.png](http://i67.photobucket.com/albums/h283/SwordRaven/Screenshot.png)

its not my screenshot  but its the same thing i'm having

Anyone else have any other suggestions ? 

*[SIZE="1"]PS. gfx drivers working as expected and glxgears reports 3800fps[/SIZE]*

TIA

---

### Post by Corvias on 2007-07-19
Are you by any chance running beryl or xgl? Try turning those off. This looks very similar to a problem I was having with my ATI x300 based laptop. Also, try rolling back a version on your ATI drivers.

---

### Post by Jonq on 2007-07-20
> **Corvias said:**
> Are you by any chance running beryl or xgl? Try turning those off. This looks very similar to a problem I was having with my ATI x300 based laptop. Also, try rolling back a version on your ATI drivers.

thanks, I edited out the things i have put into gdm.conf-custom and login screen returned to normal :)

---

