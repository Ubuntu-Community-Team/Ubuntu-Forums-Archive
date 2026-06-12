---
title: "breaks in KDE menu while selecting.."
date: 2006-10-31
forum: Desktop Environments
---

### Post by sands on 2006-10-31
Hi, while selecting from the KDE menu, I see breaks in the selection.. This is very irritating.. How to remove these..

---

### Post by aysiu on 2006-10-31
Has this always happened? Did something happen recently before the breaks started occurring? Does this happen for a new user as well (create a test user if you don't have a second user)? Do you have the proper video drivers installed (Nvidia/ATI, for example)?

---

### Post by sands on 2006-10-31
> **aysiu said:**
> Has this always happened? Did something happen recently before the breaks started occurring? Does this happen for a new user as well (create a test user if you don't have a second user)? Do you have the proper video drivers installed (Nvidia/ATI, for example)?

Thnx for the reply..
If 1 or 2 applications are opened, then there is no problem. This occurs when more than 3 apps are opened.. even the open applications file, edit.. menus have the same prob.. 
I donno abt the video drivers.. In Display system settings under Hardware tab, it shows
Graphics card: i810
driver : i810
Monitor : plug n play

My RAM is 256MB and processor is PIII

---

### Post by aysiu on 2006-10-31
I'm still curious about some of the other questions:

Has this always happened (since when you first installed Kubuntu) or only recently?

Create a test user. Does this other user have the same problem?

---

### Post by sands on 2006-10-31
> **aysiu said:**
> I'm still curious about some of the other questions:

Has this always happened (since when you first installed Kubuntu) or only recently?

Create a test user. Does this other user have the same problem?


I tested with other user account.. There is no such problem, when I opened 20 apps at a time..

In the previous installation this happened.. Now, after a long time I see this again..

---

### Post by TheWizzard on 2006-10-31
> **sands said:**
> I tested with other user account.. There is no such problem, when I opened 20 apps at a time..

In the previous installation this happened.. Now, after a long time I see this again..

back-up /home and /etc before you try anything! 

then it's probably something in your personal settings. kde-settings are in ~/.kde so probably deleting this folder could do the trick. logout and do a 
"console login" first.

but i would advice you not to delete this foldwer at the moment. it's quite likely other people will show you better ways to get rid of this problem

---

### Post by aysiu on 2006-10-31
Rather than deleting ~/.kde, just rename it: ```
mv ~/.kde ~/.kde.broken
``` Then, log out and log back in again.

---

