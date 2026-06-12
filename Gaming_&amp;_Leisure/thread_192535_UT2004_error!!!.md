---
title: "UT2004 error!!!"
date: 2006-06-08
forum: Gaming &amp; Leisure
---

### Post by davidswe on 2006-06-08
I just finished installing ut2004 and when I attempt to run it, I get the following error:[COLOR="Red"]**Couldn't run UT2004 (ut2004-bin). Is UT2004_DATA_PATH set?**[/COLOR] Does anyone have any answers for this? I really want to use Ubuntu 6.06 but I never had any problems with UT2004 in Breezy.:confused:

---

### Post by deathbyswiftwind on 2006-06-08
I will try and install it in the morning. I had it on dapper with the dist upgrade from breezy and it all worked fine let me check it out and ill get back to you tommorow morning

---

### Post by davidswe on 2006-06-09
In the interest of closing this thread, I found that the ut2004.bin file in the ut2004/system directory didn't have the proper permissions. When I checked off execute, the program ran perfectly. How it didn't have execute permission is unknown. Strange to be sure.

---

### Post by xeta on 2006-07-07
> **davidswe said:**
> In the interest of closing this thread, I found that the ut2004.bin file in the ut2004/system directory didn't have the proper permissions. When I checked off execute, the program ran perfectly. How it didn't have execute permission is unknown. Strange to be sure.

Worked for me too. Thanks for posting the fix. This may be due to patching the game. (At least, I patched it prior to starting the game) which may have overridden the default permissions.

---

