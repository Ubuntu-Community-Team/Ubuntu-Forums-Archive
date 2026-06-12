---
title: "Desktop icons position not being saved after upgrade to 13.04"
date: 2013-05-25
forum: Desktop Environments
---

### Post by sean.clarke on 2013-05-25
Hi,
    I have an installation of 5 machines and all of these exhibit the same issue - it seems the position of the desktop icons always reverts to a previous position after a logout/restart.

I have several other machines and these are fine - but this one batch (all at the same location) show this same issue.

New icons when added are persisted across logouts, but again there position always reverts to where the system "decides" they should go. This reset stats is consistent i.e. when the user moves them and then logs out and back in again they are at the same reset location.

Anyone else experienced this? or know how to fix it/whats causing it?

I can't see anything in the logs - the general permissions look OK.. I really don't want to blow away their gnome profile and am looking at other ways to investigate/fix....

Many thanks
Sean

---

### Post by galgalesh on 2013-05-25
I don't know if that still works in 13.04 but right-click on desktop and uncheck "keep alligned" ?

---

### Post by sean.clarke on 2013-05-26
"Keep aligned" just gives a "snap to grid" sort of functionality - in this scenario they are completely reset to some preordained location, they are not all aligned as in some sort of ordering, it maybe how the user had them aligned before the upgrade, but now they can't reposition them and have them consistent across logouts/restarts.

---

### Post by mc4man on 2013-05-26
Obviously not a normal situation, having 5 such feels like some local config.
"how the user had them aligned before the upgrade"
Does "upgrade" mean upgrade from previous Ubuntu release or fresh install?
If former were all 5 affected upgrades from prev.?

On any of the 5 does a newly created user have such problems?( and or a guest session
Does changing themes allow icons to stick?

---

### Post by sean.clarke on 2013-05-28
Hi mc4man,
    "upgrade" means upgrade - the previous working config was running 12.04.2 LTS, we upgraded to 12.10 and then 13.04 (as two separate upgrades carried out back to back with the users logging in to ensure any desktop "changes" would be executed.... before they logged out and we went to 13.04) - does that make sense?

I did try changing the theme, and then reselecting the generic one to "refresh" it, but I didn't do any testing with the new theme selected.

Yes, very odd - 5 machines and 5 separate user accounts.

I will create a new user and report back.

Thanks again for your assistance.

---

### Post by sean.clarke on 2013-05-31
OK - I have created a new user, create some folders on the desktop and position them in the centre and far corners, log out and back in again and they have defaulted to the left hand side.

So, it looks like some form of setting/config - especially in lieu that this 5 machine setup is the only system that exhibits this behaviour.

Anyone have any ideas how I can rectify it?

---

### Post by sean.clarke on 2013-06-01
Any ideas on how to reset this or what setting would give the same effect?

---

