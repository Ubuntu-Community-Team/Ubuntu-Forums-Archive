---
title: "Duplicate Entries in GDM Session Chooser"
date: 2010-03-15
forum: Desktop Environments
---

### Post by whshao on 2010-03-15
I installed Ubuntu Karmic and then installed xfce4, along with its dependencies. Then I found out that xubuntu-desktop is probably a better choice because of the packaged icons and themes. I didn't know if the original XFCE would make it heavier on the resources, so I removed it and all its dependencies by apt-get purge after looking at /var/log/apt/term.log.

Then I installed xubuntu-desktop, which also seems to use the GDM, except with a beautiful blue theme. Logging in works. But now I get two entries of "Xfce Session" on the session chooser box.

I've been to /usr/share/xsessions and there's only one xfce.desktop file. Is there another place that configures this? Would this be under a hidden configuration directory under the home directory?

Thanks for your help.

---

