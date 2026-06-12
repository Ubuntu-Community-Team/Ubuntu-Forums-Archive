---
title: "Prevent Unity from auto maximizing (auto maximize) windows"
date: 2012-05-10
forum: Desktop Environments
---

### Post by silviobandeira on 2012-05-10
Install gconf-editor and uncheck:

/apps/metacity/general/auto_maximize_windows

log out and log back in.
That's it. 
HTH

--
Silvio Bandeira

---

### Post by 3Miro on 2012-05-10
I believe this has been done by default on 12.04, I don't have any annoying auto-max windows.

Good to know for 11.10 though, as many people are still using it.

---

### Post by Lorin Ricker on 2012-05-13
> Install gconf-editor and uncheck:

/apps/metacity/general/auto_maximize_windows

This worked great for me. Thank you.  Auto_Maximize_Windows was indeed turned on (checked) for my install of 12.04 & Unity.

Applying the Principle of Least Surprise, the Unity developers *should'a* turned this off by default!  But then, Unity seems to break this Principle in many creative ways!  ;)

---

