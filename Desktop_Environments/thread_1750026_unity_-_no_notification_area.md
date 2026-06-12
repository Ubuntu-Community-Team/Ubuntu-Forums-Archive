---
title: "unity - no notification area"
date: 2011-05-05
forum: Desktop Environments
---

### Post by kruz_cz on 2011-05-05
Hi,

after upgrade from older version of 32-bit desktop Ubuntu (dist-upgrade from Maverick to Lucid, after reboot from Lucid to Natty) I'm trying to use Unity, but can't see any notifications, even Skype have no icon where it should be. 

- this is not whitelist issue, I tried to set it to ['all'] or set exact applications here but it didn't help

- some people report that they see the Skype icon as a 1 pixel icon, that's not my case, I simply don't see it and clicking in the empty space where the icon should be don't do anything

- I use 2 monitors, default icons like bluetooth, battery of my notebook or network manager are on both monitors (silly but can live with it), but applications notifications (Skype etc.) are nowhere

I'll appreciate any help.
Thanks

---

### Post by jeff_themovie on 2011-05-05
I'm experiencing the same issue, and it appears to be because of the dual monitor setup. I've filed a bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778256](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778256)

---

### Post by kruz_cz on 2011-05-06
yes I can confirm that, notifications appears when I turn off external monitor in nvidia control panel and drop out when I turn it back on.

Dell E6400 with Nvidia Quadro NVS 160M

---

### Post by pgmac on 2011-05-08
I have this same problem as well.
Before I noticed this and found the unity whitelist (via dconf-editor), I tried gnome3 from the gnome3-team ppa.
After finding it didn't work with my graphics card (cheap and nasty ATI), I used ppapurge to deinstall gnome3.
After this, the notification area has not displayed.  I'm not sure if it was there prior to installing (and deinstalling) gnome3, though.

I do have a dual monitor setup and tried disconnecting the second monitor, but this didn't help me either.

I tried setting my whitelist to ['all'] and it still didn't display.  This also gave other problems with the panel (not showing all items on the second monitor).  After setting it back to Default again and adding some other applications, I still don't have the notification area.

Cheers,
Paul

---

### Post by kruz_cz on 2011-05-09
Jeff I have the same setup of monitors as you have (looked at the screenshot on launchpad) and there is a workaround for us - move the position of your laptop monitor to the top of the desktop. Probably it will not come up to your hardware setup of monitors, but as addition it looks like panel on the desktop monitor works better now (shows up all it should show except the old notification area).

---

### Post by jeff_themovie on 2011-05-09
> **kruz_cz said:**
> Jeff I have the same setup of monitors as you have (looked at the screenshot on launchpad) and there is a workaround for us - move the position of your laptop monitor to the top of the desktop. Probably it will not come up to your hardware setup of monitors, but as addition it looks like panel on the desktop monitor works better now (shows up all it should show except the old notification area).

Thanks, I finally broken down and arranged my (logical) screens as you suggested. It fixes other dual-monitor annoyances (like when I throw my mouse cursor up it goes into the dead space instead of stopping at the Unity global menu).

But now it doesn't match how my equipment is physically arranged, so I'll need to get use to my mouse cursor "jumping" up and down every time it crosses to the other screen :(

---

### Post by kruz_cz on 2011-05-09
I'm in the same situation, so I added a hardware upgrade to this workaround - used a pack of office paper as a foot for my notebook :D Not so much pretty, but I hope unity developers will fix that bug soon.

---

### Post by pgmac on 2011-05-11
Well there you go, I arrange my screens, so my main screen (laptop screen) was at the top of the virtual window as well and after a reboot, I had some of my notify icons again.
So, I went back into dconf-editor again, to add some other applications I wanted to appear in there and they've gone again.
Seems to be a mix of icons in there that will cause some manner of issues.

Either way, at least it's a step in the right direction.  Hopefully we'll either get a proper solution to this, or all apps will be using the appindicator instead.

---

