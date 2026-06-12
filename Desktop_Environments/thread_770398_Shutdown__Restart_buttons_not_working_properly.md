---
title: "Shutdown / Restart buttons not working properly"
date: 2008-04-27
forum: Desktop Environments
---

### Post by slazh on 2008-04-27
I hope this is the right section for this question. If it's not then .. well.. please tell me what is :)

I upgraded my mom's machine yesterday to 8.04. The machine was running xubuntu 7.10 before so I upgraded the usuall way. All went fine except for one part, which is kind of annoying: when I choose Applications > Quit and then either Shutdown or Restart, I get back to the login screen. The system does not reboot, nor shutdown, no mather how long you wait.

The strange thing is that when I'm at the login window, I can shutdown / restart the machine fine with the options given at the login screen.

Does anybody know how to fix this?

---

### Post by weslson on 2009-02-25
bump

---

### Post by kwikshot on 2011-06-15
Old I know but bump for Xubuntu 11.04

---

### Post by Toz on 2011-06-15
I don't have a solution, but I can provide some background on the issue. Whats really happening behind the scenes is that X is crashing before the shutdown/reboot command is executed, and the automatic response is to respawn the x session - leading to a redisplay of the login screen.

This is a known bug ([https://bugzilla.xfce.org/show_bug.cgi?id=7442]("https://bugzilla.xfce.org/show_bug.cgi?id=7442")) that has been fixed upstream in version 4.8.2 (I believe). Unfortunately, the fix introduces transparency issues ([https://bugzilla.xfce.org/show_bug.cgi?id=7534]("https://bugzilla.xfce.org/show_bug.cgi?id=7534"))

Looks like some sort of bad interaction between X and xfdesktop. I'm not exactly sure of how they're moving forward with this, but it may require some fixes both with xcfe and X.

The interesting thing is that this bug is intermittent (on my machines at least). Sometimes it crashes and sometimes it doesn't (meaning I can successfully shutdown/reboot). There doesn't appear to be any clear correlation between action and result. I find that I am more successful if I shutdown/reboot from the menu Logout option than I am from the Session Menu Logout option.

---

