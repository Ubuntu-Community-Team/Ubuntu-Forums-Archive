---
title: "Unable to run Emerald at startup 9.10"
date: 2009-12-11
forum: Desktop Environments
---

### Post by Konichiwa on 2009-12-11
Hey all,

I am unable to get emerald to run at startup.

I have tried editing compiz settings manager with emerald -replace and that worked for one reboot, then it stopped working.

Is there another way for 9.10 to get emeral to run at startup?

I seem to remember somewhere setting custom startup services, I think that might work but I am unsure and do not know how to do it.

Thanks

---

### Post by j7%&lt;RmUg on 2009-12-11
Make sure its:

emerald --replace

and not:

emerald -replace

if the above is set and it still doesnt work right, then try leaving that setting blank and adding the emerald --replace command in System > Preferences > Startup Applications instead.

---

### Post by j7%&lt;RmUg on 2009-12-11
Make sure its:

emerald --replace

and not:

emerald -replace

if the above is set and it still doesnt work right, then try leaving that setting blank and adding the emerald --replace command in System > Preferences > Startup Applications instead.

---

