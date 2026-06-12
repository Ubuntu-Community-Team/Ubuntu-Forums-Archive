---
title: "No automatic suspend after inactive timeout from lock and login screen GDM"
date: 2014-08-16
forum: Desktop Environments
---

### Post by RobertFM on 2014-08-16
Suspend is not kicking in after set inactive timeout of X minutes when the lock
screen is already activated. pm-suspend.log has no mention of the system even
trying to suspend.

Suspend does work when inactive timeout of X minutes to suspend is less then X
minutes to blank/lock screen. Suspend also works when the screen is locked and
I close the lid. 

Would love to fix this last issue. If I can get it fixed I'd have the first
(near)perfect system in years.

Update 17-8-'14:
I managed to get suspend working from the lock screen by editing /etc/systemd/logind.conf and un-commenting and changing minutes:
IdleAction=suspend
IdleActionSec=15min

I now just need to find a way to increase the IdleActionSec when my laptop is on ac power. 

Any ideas anybody?

---

### Post by stiv2k on 2015-06-30
Problem still persists as of June 2015, and can confirm your solution still works too.

---

