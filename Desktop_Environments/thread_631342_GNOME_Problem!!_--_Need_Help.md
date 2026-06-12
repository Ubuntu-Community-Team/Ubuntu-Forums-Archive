---
title: "GNOME Problem!! -- Need Help"
date: 2007-12-04
forum: Desktop Environments
---

### Post by subs on 2007-12-04
when i try to start my computer.... i get this error message.....

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.


the theme i had applied to my desktop seems to have gone away......

i tried to open the Appearance window from System > Preferences > Appearence 
i got this error message....

> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

i have not tried to install KDE..... only thing i can remember is downloading a update for gnome from the ubuntu update manager

i have however installed this software called kmobiletools..... is that causing the problems!!??:confused::confused:

---

### Post by kshane on 2007-12-04
> **subs said:**
> when i try to start my computer.... i get this error message.....




the theme i had applied to my desktop seems to have gone away......

i tried to open the Appearance window from System > Preferences > Appearence 
i got this error message....



i have not tried to install KDE..... only thing i can remember is downloading a update for gnome from the ubuntu update manager

i have however installed this software called kmobiletools..... is that causing the problems!!??:confused::confused:

Do you get the same error message when you reboot?

Kevin

---

### Post by subs on 2007-12-05
well.... it comes and goes....

some times it stays after the reboot.....

some times it goes away

---

### Post by dast on 2007-12-06
I just upgraded from 7.04 to 7.10 and I can confirm this bug happened to me

$uname -a
Linux wolf 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

See the following bugs.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277)

Unlike some people, I found that i could start the daemon from the command line. So... I "fixed" the problem by going under System > Preferences > Sessions (in the main Gnome menu) and adding a startup program entry for the daemon. That does not work for everyone, apparently. Others have hacked up init.d scripts (i believe) to start this daemon, which I opted not to try.

See also
[http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon)

---

