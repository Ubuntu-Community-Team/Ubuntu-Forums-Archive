---
title: "Flaky unity dock on 12.04"
date: 2012-04-30
forum: Desktop Environments
---

### Post by mvidberg on 2012-04-30
Just updated to 12.04 and I use auto-hide for my unity dock/launcher.  I've noticed that it is actually difficult to get it to appear now... seems kinda flaky.  I have to move the mouse over to the left and then "rub" up and down to make it appear.  This is very annoying.  My solution was to set it to only come up on going to top-left corner, which makes it even harder to make show up, and just click the Windows key on my keyboard when i need it.  I just use glx-dock so the times when I need the unity dock is almost never anyway.

---

### Post by amr-maro on 2012-04-30
It is _**NOT**_ about how _**hard**_ you push the mouse cursor, it about how _**far**_ you push. To be able to reveal the launcher, you have to _***continuously***_ push the cursor against the edge to reveal it.

To fix the launcher reveal sensitivity:
a. Install then start "CompizConfig Settings Manager"
b. Navigate to "Desktop" > "Ubuntu Unity Plugin" > "Experimental" tab
c. Find the string "Launcher Reveal Pressure"
d. The default is 20, change it to 7 (or whatever you prefer)
e. You don't have to close CCSM to apply the changes. Keep changing the value till you are satisfied with the result, then close CCSM.

Please spread & share this post if you find it helpful :)

---

### Post by 00negative on 2012-04-30
I have had this issue as well, I will have to try the proposed fix when I get home.

---

### Post by mvidberg on 2012-04-30
Thanks amr-maro!  That setting did the trick.

---

