---
title: "delayed logout with xfce on 14.04"
date: 2014-08-24
forum: Desktop Environments
---

### Post by Dr Kayak on 2014-08-24
I just installed Ubuntu 14.04 and Xfce4, and have a recurring problem when logging out:  after selecting *log out* in the dialogue box, the logout happens immediately, or after 10-15 seconds, or after about one minute, with no pattern that I can recognize.  This happens both when I select *log out* from the Applications Menu, and when I do [FONT=Courier New]xfce4-session-logout[/FONT] (including the possible options [FONT=Courier New]--logout[/FONT] and [FONT=Courier New]--fast[/FONT]).  I do not see this delay when I log out from the Unity desktop.  Please help!

---

### Post by atp2 on 2014-08-24
I see the same behavior on my Xubuntu 14.04.1 laptop.  Other peoplef report similar problems for (at least) all Xubuntu versions from 11.10 through 14.04:

  [https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1013548](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1013548)
  [http://askubuntu.com/questions/380140/xubuntu-13-10-64bit-slow-and-buggy-log-out-process](http://askubuntu.com/questions/380140/xubuntu-13-10-64bit-slow-and-buggy-log-out-process)
  [https://bugs.launchpad.net/upstart/+bug/1227212/comments/2](https://bugs.launchpad.net/upstart/+bug/1227212/comments/2)

I haven't tried it yet, but one reported (2013-09-18) workaround is that commenting out xubuntu from /etc/upstart-xsessions leads to normal logout and login speeds.

Also, while waiting for the logout, shutdown, or other command to actually take effect, if I try to use the logout menu again it pops up an error message saying:

```

Failed to run action "Log Out"
"Session manager must be in an idle  state when requesting a shutdown"

```

Btw, doing "sudo shutdown -r now" works normally without any slowdown, so the problem does seem to be X specific.

---

### Post by Dr Kayak on 2014-08-25
Many thanks for the tip ... commenting *xfce* in [FONT=Courier New]/etc/upstart-xsessions[/FONT] solved the problem for me.

[Apologies:  I could not figure out how to mark this thread as SOLVED, even after google searches.]

---

