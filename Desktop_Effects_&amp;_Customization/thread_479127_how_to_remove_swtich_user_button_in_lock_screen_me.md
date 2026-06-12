---
title: "how to remove swtich user button in lock screen menu ?"
date: 2007-06-20
forum: Desktop Effects &amp; Customization
---

### Post by ashwin_cse on 2007-06-20
Hi,

I have configured my desktop preference to start screen saver when desktop is inactive for 5 minutes & to lock the screen when screen saver is active. Now when i move the mouse when the screen saver is active i am presented with a menu to enter password to reach desktop. This is fine, but there is option to switch user. People here are using this option to use my pc. Although they are not using my account, the pc is in their hands & i am locked out of pc. I dont want this to happen. So in order to avoid this situation i must remove the switch user button, so that when they want to use my pc they ask me.

with regards,
ashwin

---

### Post by marc321 on 2007-06-20
Hello.

Press Alt-F2 to start the run dialog.  Enter *gconf-editor* into it and press enter.  In the window that comes up, click the arrow next to "apps." Find "gnome-screensaver" in the list and click it.  In the pane at the right, scroll down to the bottom.  Uncheck "user_switch_enabled."

That's it!  Let me know if it works for you.

EDIT: Well, it should have worked, but apparently there's a bug in Feisty that causes this to not work.  Here's a link to the actual bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/114945]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/114945")

Sorry about that.  :(

---

### Post by vertigo1980 on 2007-06-21
my sister just tried to "switch user" while my pc was locked. due to another beryl/compiz bug that more or less 'crashes' the pc when a user tries to switch (or switches out, then switches in again). restarting x didn't work, the only option was a hard reset. :mad:

now i try to get rid of the switch user button and encounter yet another (this) bug. how long does it usually take for things like these to get fixed?

---

