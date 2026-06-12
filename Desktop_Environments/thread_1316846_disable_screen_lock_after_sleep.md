---
title: "disable screen lock after sleep"
date: 2009-11-06
forum: Desktop Environments
---

### Post by sca33 on 2009-11-06
I've searched for possible solutions, and this did _not_ help:

- uncheck all (use_screensaver_settings, suspend, blank screen, etc...) in gconf-editer /apps/gnome-power-manager/lock
- check disable_lock_screen in /desktop/gnome/lockdown
- LOCK_SCREEN=false in /etc/default/acpi-support

It's still show password prompt after I wake my laptop from sleep.

what else should I try?

//ubuntu 9.10

---

### Post by sca33 on 2009-11-08
up

---

### Post by Altay_H on 2009-12-02
I'm having the same problem. This is a particularly irritating bug because not even the hackish workarounds do anything to change the situation.

---

### Post by eris23 on 2010-01-21
System - Preferences - Screensaver
Needed to uncheck "Lock screen when screensaver is active"

---

### Post by riseringseeker on 2010-01-25
> **eris23 said:**
> System - Preferences - Screensaver
Needed to uncheck "Lock screen when screensaver is active"

I've done all of the above, and it **still** asks for a password from suspend.  I even rebooted to make sure the settings were kept, they were.  It comes back from suspend to a screen saver, but then asks for a password, even though it doesn't if I just let the screensaver activate with the timer.

---

### Post by mcduck on 2010-01-25
There's a bug in the indicator-applet-session (the panel applet with shutdown buttons etc) that causes it to lock the screen when suspending (or switching users etc), regardless of what the actual gconf settings for screen locking are.

Currently there's no workaround other than using some other means to suspend the machine than through that applet.

---

### Post by riseringseeker on 2010-01-25
> **mcduck said:**
> There's a bug in the indicator-applet-session (the panel applet with shutdown buttons etc) that causes it to lock the screen when suspending (or switching users etc), regardless of what the actual gconf settings for screen locking are.

Currently there's no workaround other than using some other means to suspend the machine than through that applet.

Yeah, I found that out.  The laptop works fine to resume passwordless from suspend if I do an Fn-F1 of close the lid.  Working on getting suspend to work on the desktop now...

---

### Post by riseringseeker on 2010-01-29
> **mcduck said:**
> There's a bug in the indicator-applet-session (the panel applet with shutdown buttons etc) that causes it to lock the screen when suspending (or switching users etc), regardless of what the actual gconf settings for screen locking are.

Currently there's no workaround other than using some other means to suspend the machine than through that applet.

I have since found an easy way around it, at least if your running Karmic (don't know about earlier releases).  Just hit CTRL-ALT-DEL, that brings up a menu much like the indicator-applet-session would.  Suspending that way the system will not ask for a password when coming out of suspend, assuming you have it set that way.

---

### Post by marianomd on 2010-04-29
Open up gconf-editor

Go to /apps/gnome-power-manager/lock/

Uncheck suspend and hibernate.

Cheers.

---

### Post by MountainX on 2010-06-25
Here's my solution. It works on the Gateway LT2115u (LT-Series) which is a rebranded Acer Aspire One 532h.

Open the terminal, and type gconf-editor. Do NOT use sudo or you will not change the settings for your own user account!
In the left pane of the window that comes up go to apps > gnome-power-manager > lock .
On the right, UNCHECK suspend and hibernate and everything else except for use_screensaver_settings (this is the only one that is CHECKED)

Now go to main menu: system > preferences > screen saver
At the bottom of the window that comes up, uncheck "lock screen when screensaver is active"

The following commands *should* do the same thing...
```

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/gnome_keyring_hibernate false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/gnome_keyring_suspend false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/hibernate false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/suspend false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings true
gconftool-2 --type boolean -s /apps/gnome-screensaver/lock_enabled false
```

---

### Post by tani1981 on 2010-08-23
Do not know if you guys already solved this but I have a fix. Obviously you're not doing it right. Open gconf editor, do the above steps at apps., where you uncheck all 3 locks (screensaver, suspend and hibernate), but you also have to step back to main tree of gconf editor, desktop, gnome, lockdown, and finally check the: disable_lock_screen. Then reboot and try to suspend, no prompt screen should appear and it should take you to your desktop.

---

### Post by crtlbreak on 2010-09-02
Settings are immediate - this is not windoze ....You wont need to reboot
;)

---

### Post by mistafeesh on 2010-09-14
Thanks guys, just came looking for that info, and that did the trick for me - had to do what tani1981 said too, before it was fixed. 

What a relief! My laptop has a borked keyboard and I am currently using synergy with it from a mac. Had to plug in a kb to log in before I could carry on with work....

---

### Post by Cherry Cotton on 2010-10-20
> **tani1981 said:**
> Do not know if you guys already solved this but I have a fix. Obviously you're not doing it right. Open gconf editor, do the above steps at apps., where you uncheck all 3 locks (screensaver, suspend and hibernate), but you also have to step back to main tree of gconf editor, desktop, gnome, lockdown, and finally check the: disable_lock_screen. Then reboot and try to suspend, no prompt screen should appear and it should take you to your desktop.

That really seems like overkill, though; in order to prevent the screen from locking when I don’t ask it to, I have to prevent the screen from locking at all.

I wish they’d fix this stupid bug >_<

---

### Post by menu on 2011-05-07
@MountainX thank you! That fixed it for me! And a big thanks to the 11.04 developers for fixing the suspend/screen blank problems in this new release

---

### Post by KNtim on 2011-05-10
Made the SAME mistake the previous poster pointed out. DO NOT USE SUDO when launching GCONF-EDITOR. Then uncheck the appropriate boxes.
Thanks!
 They really need to fix this bug so I can just shut it off in the Screensaver settungs. Have have this happen in several itterations of Ubuntu.
Running 11.04 Natty Narwhal

---

### Post by sup on 2011-05-29
> **mcduck said:**
> There's a bug in the indicator-applet-session (the panel applet with shutdown buttons etc) that causes it to lock the screen when suspending (or switching users etc), regardless of what the actual gconf settings for screen locking are.

Currently there's no workaround other than using some other means to suspend the machine than through that applet.

For anyone interested, it is this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228)

---

### Post by techknowledge on 2012-01-25
> **MountainX said:**
> Here's my solution. It works on the Gateway LT2115u (LT-Series) which is a rebranded Acer Aspire One 532h.

Open the terminal, and type gconf-editor. Do NOT use sudo or you will not change the settings for your own user account!
In the left pane of the window that comes up go to apps > gnome-power-manager > lock .
On the right, UNCHECK suspend and hibernate and everything else except for use_screensaver_settings (this is the only one that is CHECKED)

Now go to main menu: system > preferences > screen saver
At the bottom of the window that comes up, uncheck "lock screen when screensaver is active"

The following commands *should* do the same thing...
```

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/gnome_keyring_hibernate false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/gnome_keyring_suspend false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/hibernate false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock/suspend false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings true
gconftool-2 --type boolean -s /apps/gnome-screensaver/lock_enabled false
```

I wanted to thank you for the quick command list for committing the lock screen/blank screen as well as the hibernate/suspend information. It worked well on 32-Bit Desktop Edition on 11.04 Natty and 11.10 Oneiric.

---

