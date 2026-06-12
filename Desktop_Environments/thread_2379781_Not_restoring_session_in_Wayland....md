---
title: "Not restoring session in Wayland..."
date: 2017-12-09
forum: Desktop Environments
---

### Post by bedtime2 on 2017-12-09
Whenever I restart the computer or try to log into a Wayland session, I am reverted right back into the login prompt. When it first happened, I thought I had mistyped my password; I had  retyped it about half a dozen times, after which, I found that logging into an  Xorg session worked fine.


I have Ubuntu 17.10 installed, and I am using the stock Gnome instead of the default Ubuntu Gnome. I use 10 static workspaces, and I used dconf Editor to activate the session restore mode:

*/org/gnome/gnome-session/auto-save-session [ -> ON]*


Is there a way to restore a session in Wayland?


Thank you.

---

### Post by deadflowr on 2017-12-09
The saved sessions is not a wayland issue per se, but a general problem for gnome since it switched to gnome3.
The unreliability of it is why they removed it as a startup application you could toggle (an subsequently buried the setting in dconf/gsettings for those who would want to risk any downfall that may come from enabling the behavior. )

The login loop is probably a result of using an unsupported (unsupported by wayland that is) graphics driver.
Though I thought a fix was released to ensure a system that cannot run wayland properly will automatically log into the xorg session. regardless of which session was selected.

Is the system fully up to date?

---

### Post by bedtime2 on 2017-12-10
Thank you; this is quite informative! :)

It seems that logging into an Xorg session with auto-save-session turned on does NOT work recover anything (as you mentioned would likely be the case), but I question that Wayland is not running correctly, though I could be wrong in this:

When running with auto-save-session turned off, and when in a Wayland session, I used the command *loginctl show-session 1 -p Type*, and the response was *wayland*, at that time, so unless that check was incorrect, I believe Wayland is running fine and that there is no graphics driver problem. It seems to only toss me back into login when auto-save-session is on (off is fine).

You make a good point that having to go into dconf to do such a common task is quite  indicative that the task is not up to par, which is a shame. *Startup applications* will not resolve this as I would like to have apps open in different workspaces, but I like that you mentioned it.

Yes, the system is fully up to date.

I may have to look into using KDE for this. Please let me know if you find anything else pertaining to this or if you have any other solutions—I appreciate your efforts!

:KS

---

### Post by deadflowr on 2017-12-10
I've used (still use) this gnome extension to allow placing windows to open only in specific workspaces:
[https://extensions.gnome.org/extension/16/auto-move-windows/]("https://extensions.gnome.org/extension/16/auto-move-windows/")
then in conjunction with that I set the apps I want to open at startup in Startup Applications and then those will open in the specified workspace.
(I use tweak tool to set it up, since it's fairly easy to do with that, though I'm sure it's doable through dconf)
fwiw

Here's a long standing bug on auto save session:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/771896]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/771896")

I'm sure wayland is just being wayland; young and infant, so it's probably buggy all on it's own anyway.
I'd avoid it and just login with Xorg, only periodically checking wayland if running wayland does nothing but give me a giant headache.

Current discussion on wayland for the next release here:
[https://ubuntuforums.org/showthread.php?t=2379557]("https://ubuntuforums.org/showthread.php?t=2379557")
another fwiw

Just some random thoughts anyway.

---

### Post by bedtime2 on 2017-12-10
> **deadflowr said:**
> I've used (still use) this gnome extension to allow placing windows to open only in specific workspaces:
[https://extensions.gnome.org/extension/16/auto-move-windows/](https://extensions.gnome.org/extension/16/auto-move-windows/)
then in conjunction with that I set the apps I want to open at startup in Startup Applications and then those will open in the specified workspace.
(I use tweak tool to set it up, since it's fairly easy to do with that, though I'm sure it's doable through dconf)
fwiw
Great extension! This works fine for me, but it does not work under Wayland—it will only open certain applications.

> Here's a long standing bug on auto save session:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/771896](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/771896)

I'm sure wayland is just being wayland; young and infant, so it's probably buggy all on it's own anyway.
I'd avoid it and just login with Xorg, only periodically checking wayland if running wayland does nothing but give me a giant headache.

Current discussion on wayland for the next release here:
[https://ubuntuforums.org/showthread.php?t=2379557](https://ubuntuforums.org/showthread.php?t=2379557)
another fwiw

Just some random thoughts anyway.
I will have to wait until Wayland is more stable. For now, I'll use the Gnome extension you recommended.

Thanks!

---

