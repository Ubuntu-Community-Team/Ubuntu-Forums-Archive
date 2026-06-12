---
title: "GNOME System Quit"
date: 2008-02-05
forum: Desktop Environments
---

### Post by BRRFOC on 2008-02-05
Gnome menu System Quit hangs after for 1 minute after 1st key selection, and popup doesn't list option for suspend/hibernate.  After this, System Quit works normally.  Problem arose after recent updates:xserver-xorg-core, hwdb-client-gnome_0.6.11.1_all, hwdb-client-common_0.6.11.1_all, libc6_2.6.1-1ubuntu10_i386, gnome-panel_1%3a2.20.1-0ubuntu1_i386, gnome-menus_2.20.1-0ubuntu1_i386, gnome-desktop-data_1%3a2.20.1-0ubuntu1_all.

Any ideas?

---

### Post by nilarimogard on 2008-02-05
I had that problem too when i installed xcompmgr and a few other things, but wasn't sure if that was what caused it. Did you install xcompmgr also?

---

### Post by Fraktyl on 2008-02-05
I started having that problem also.  The system doesn't actually lock up, so I hit CTRL-ALT-F1 to go to a text session.

Logged in and typed tail .xsession-errors

My problem was I had turned off the power management in the session properties.  For some reason the gnome session manager was trying to communicate with it, and it never responded, hanging the session.

I turned the power management back on until I can figure out how to remove the power management daemon without causing the log out to hang.

---

### Post by BRRFOC on 2008-02-05
Many thanks Fraktyl, will try your suggestion to activate Power Management.  Curious this problem occurs upon first use of button but not afterwards.

---

