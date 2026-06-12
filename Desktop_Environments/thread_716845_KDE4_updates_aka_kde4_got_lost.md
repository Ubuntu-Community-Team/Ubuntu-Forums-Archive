---
title: "KDE4 updates aka kde4 got lost"
date: 2008-03-06
forum: Desktop Environments
---

### Post by markoloka on 2008-03-06
Bunch of kde4 updates came today... now there's still 9 left  and adept updater won't upgrade them. I saw there was updates that said remove in "requested". Seems that they updated (read: got removed) well BUT now i can't choose kde4 in login screen as there is no kde4 to choose anymore. I guess kde4 is still installed in my kubuntu 7.10 but how can i get it up and running???

---

### Post by fuji on 2008-03-08
There's a transition to libgif which has broken KDE4 and a whole lot of other things.  I can't install a bunch of stuff right now because of this.

[https://bugs.launchpad.net/ubuntu/+source/libungif4/+bug/174252](https://bugs.launchpad.net/ubuntu/+source/libungif4/+bug/174252)

You can try installing fluxbox or some other DE, or if you still have parts of KDE3 you can use that.

EDIT: 
Turns out the update removed kdebase-workspace which basically removes all of KDE4 that is needed to log in from KDM.  So, a re-install of that should work

---

