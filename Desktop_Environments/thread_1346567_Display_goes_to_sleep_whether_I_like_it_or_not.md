---
title: "Display goes to sleep whether I like it or not"
date: 2009-12-05
forum: Desktop Environments
---

### Post by Zercius on 2009-12-05
Okay. I'm running Xubuntu on my Eee PC and in the Xfce Power Manager I have all power settings set to "Never" on AC power. I also disabled the screensaver. On a side-note: why do we still have competing screen saver and power management settings? Regardless of any of these settings, my display still goes black after 10 minutes (I timed it). 

Any ideas what could be causing this? Places I should be looking? I was wondering if somehow the screensaver was getting activated anyways, so I completely removed the various screensaver packages.

---

### Post by Zercius on 2009-12-06
Okay, I think I figured it out. With Karmic no longer having an Xorg.conf, the default power management capabilities of X.org are being enabled again. This includes blanking the screen after 10 minutes. Here is some more information:

[http://www.shallowsky.com/linux/x-screen-blanking.html]("http://www.shallowsky.com/linux/x-screen-blanking.html")

So far I've just done:
```

sudo xset s 0 0

```
To disable the Xorg "screensaver". It does seem to work; it's been more than 10 minutes with no screen blanking. Since xset works on a per-session basis, I made a stub Xorg.conf to set at least the BlankTime perminantly:
```

Section "ServerFlags"
	Option		"BlankTime"	"0"
EndSection

```
When I was using xscreensaver, either it or xfce-power-management should be disabling the Xorg built-in screen blanking. Unless anyone else has any relevant feedback, I'll probably report this as a bug.

---

### Post by mohrol on 2009-12-15
It seems I had the same problem. The screen went blank after 10min, no matter how I configured the Xfce 4 power manager or the gnome screensaver.
I purged the gnome-screensaver package and installed xscreensaver.
Turning the "Monitor power management control" option off in the Xfce 4 power manager GUI now gives me full control over screensaver, standby and off-state timings via the xscreensaver configuration and so far all of them seem to work.
It's my _impression_ that the gnome-screensaver package somehow does not fit into this environment - Unfortunately I do not fully understand the interactions involved yet.

Could you provide a link to the bugreport once you've filed it in launchpad?

---

### Post by n4pgw on 2009-12-15
My screen saver on my desktop freezes the system.  When I turned off all management to the screen saving, etc, I got the same thing, the system blanks in 10 minutes of no keyboard or mouse even in a movie.  I'll try the steps in this thread.

Thanks

Buck

---

### Post by Zercius on 2009-12-18
Posted a bug report:
[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/498366](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/498366)

---

### Post by n4pgw on 2009-12-18
> **Zercius said:**
> 

  I made a stub Xorg.conf to set at least the BlankTime perminantly:
```

Section "ServerFlags"
    Option        "BlankTime"    "0"
EndSection

```When I was using xscreensaver, either it or xfce-power-management should be disabling the Xorg built-in screen blanking. Unless anyone else has any relevant feedback, I'll probably report this as a bug.

Can you tell me where you placed this conf file?  I am a newbie and could not find a copy so I assume you created it somewhere in the filesystem.  

Thank you,

Buck

---

### Post by Zercius on 2009-12-18
> **n4pgw said:**
> Can you tell me where you placed this conf file?  I am a newbie and could not find a copy so I assume you created it somewhere in the filesystem.

Certainly. The full path should be:
**/etc/X11/xorg.conf**

As usual, you'll need to use the sudo command or equivalent to create this file as root.

---

### Post by n4pgw on 2009-12-18
OOPS, I just realized the thread is for Xubuntu and I have Ubuntu with Gnome.

---

