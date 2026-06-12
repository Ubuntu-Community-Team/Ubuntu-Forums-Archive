---
title: "power management without login"
date: 2012-07-06
forum: Desktop Environments
---

### Post by nixahn on 2012-07-06
Hi, I have been trying to understand this with google for a day now, it's time to ask. I don't fully understand how the power management works in ubuntu desktop and it's derivatives.

My question is which services influence the computer when no user is logged in but the X environment is loaded? Is the loading of the X server a trigger for the power management or is it session dependent?

I have considered the acpid and apmd but those only emit events and accept instructions. My computer goes to sleep automatically, and the idle timers are supposed to be controlled by gnome-power-manager or xfce4-power-manager processes, something like that should be playing a role. However, power managers should not be loaded when no user is logged in because they are gui apps, right? are the managers perhaps also loaded by root on startup?

The specific scenario: I have my computer temporarily set up to accept remote logins through ssh. There is no user logged in the computer itself, I can WOL the computer, log in; however, the computer goes to sleep when I disconnect from it. I am trying to get a job done which does not inhibit the computer, it is running as a process (using screen). I can never complete the task because the computer sleeps, and I can't stay hooked because I need to move the computer that connects around (and because of broken pipes due to bad network).

I tried using dbus-send, but it's a dead end since the inhibitions stop when the process exits. Since I'm on xfce, there is no "applet" like with vanilla gnome to inhibit the sleep either. In any case, I don't really want a hack like thi, it's a good opportunity to understand better which processes control ubuntu's power management and how they interact, and google is not clear on that.

thanks for any help/directions to documentation;

---

