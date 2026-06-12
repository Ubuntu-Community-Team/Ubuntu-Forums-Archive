---
title: "Configure SDDM to not show name of the last logged-in user"
date: 2018-10-03
forum: Desktop Environments
---

### Post by ericjoh on 2018-10-03
Hi,

I have installed Ubuntu 18.04 with SDDM on some machines at work. How do I configure it to not show name of the last logged-in user, i.e., so that you always have to type in the username at the login page?

Relevant packages installed:
# dpkg -l|grep sddm
ii  kde-config-sddm                                 4:5.12.6-0ubuntu0.1                         amd64        KCM module for SDDM
ii  sddm                                            0.17.0-1ubuntu7                             amd64        modern display manager for X11
ii  sddm-theme-breeze                               4:5.12.6-0ubuntu0.1                         amd64        Breeze SDDM theme

I see that the last logged-in username is store as "User=[username]" in "/var/lib/sddm/state.conf".

I have tried to set "RememberLastUser=false" in /etc/sddm.conf but it seems to have no effect because "User=[username]" is still updated in "/var/lib/sddm/state.conf".

Best regards / Eric

---

