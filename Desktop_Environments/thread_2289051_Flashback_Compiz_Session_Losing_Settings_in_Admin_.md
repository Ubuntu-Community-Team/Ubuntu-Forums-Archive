---
title: "Flashback Compiz Session Losing Settings in Admin abd Backup Accounts 14.04"
date: 2015-07-31
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-07-31
Hello,

For about the past two days my Flashback Compiz sessions have been losing all kinds of settings that
don't appear to be related.  All of my shell scripts in the home folder have been losing their execute
permissions; and I've had to go back and reset these. I've been losing panel icons in both accounts; and
Mac Slow's Cairo Clock has been losing its position information. This definitely appears to be OS rather
than application related. This instability makes me fear that my OS will eventually get hosed.  Any help
appreciated.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-01
There appears to be a problem with this package:

xserver-xorg-core-lts-utopic2:1.16.0-1ubuntu1.2-trusty2

Please see attachment.

Hannibal

Here is something else I've noticed.  When I create a launcher on the desktop, then move it to the panel
and delete the original still on the desktop, the launcher will always disappears after I reboot. I've only
noticed this behavior after the last couple of updates. However, when I create a launcher in the man menu
and then create a shortcut in the panel by dragging it from the main menu, the icon persists, even after
I uncheck it in the main menu.  Also, the main menu seems to dislike some images. I don't know whether
this is because of the file type, the size, or for some other reason.

Thanks, Hannibal

---

### Post by mc4man on 2015-08-01
I  don't use that gnome session but the idea is the same. 
When you create a .desktop on your Desktop & drag to the panel the item in the panel is a shortcut to the .desktop on your Desktop.
If you remove that .desktop file from your Desktop  then you have a shortcut to nothing so it disappears from the panel.

When you create a .desktop (launcher) in main menu it creates a file (.desktop) in ~/.local/share/applications/
It's likely that unchecking that item from main menu only removes it from the menu, not the file itself. So the  shortcut in the panel remains valid.

---

### Post by coljohnhannibalsmith on 2015-08-01
Makes sense.

---

### Post by CantankRus on 2015-08-01
When I used to experiment with many different desktops and configs and encountered odd errors, 
I would reinstall and reconfigure to get back to that point,
just to be confident something I had inadvertently done wasn't messing things up.

From your threads you appear to be trying a lot of different setups.
With some of your unusual problems, may be a good time to start a fresh.

---

### Post by coljohnhannibalsmith on 2015-08-02
I think it would be even more work to rebuild at this point.  Also, this is a dual
boot setup, and the Windows side is completely stable.

Thanks, Hannibal

---

### Post by CantankRus on 2015-08-02
> **coljohnhannibalsmith said:**
> I think it would be even more work to rebuild at this point.  Also, this is a dual
boot setup, and the Windows side is completely stable.

Thanks, Hannibal

Don't see what Windows has to do with it.
Linux is very stable also but is a lot easier to mess up when you start installing different desktops, 
adding ppas, running terminal commands etc etc.

Just a suggestion.... can't see it being any more time consuming than your situation now.

---

### Post by coljohnhannibalsmith on 2015-08-02
I thought about it for awhile, then decided that your reinstallation idea had merit; but I also
decided to start with the most obvious and reinstall xscreensaver and its associated packages
in synaptic first. When I tried to reinstall xscreensaver, synaptic warned me right-away that I
had some broken packages; so I rebooted into recovery mode and selected the option to
repair broken packages. There were 17. This time reinstallation was successful, with no alerts.
I then let xscreensaver run for a while; and there was no crash. The desktop locked-up however; so
I had to reboot again. I'm going to let things run for a while, as they are, before I mark this thread
as solved; but things are looking much better so far.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-02
I spoke to soon.  xscreensaver is still crashing; however, I did fix 17 broken packages, and that's bound
to have some beneficial effect.

---

### Post by coljohnhannibalsmith on 2015-08-02
Interesting discovery. The last time xscreensaver crashed, the login screen appeared.  It's as if someone
touched a key to log back in. What could cause this?

Thanks, Hannibal

---

### Post by CantankRus on 2015-08-02
It began doing that for me in 14.04 when compiz failed to reload correctly.

---

### Post by coljohnhannibalsmith on 2015-08-02
> **CantankRus said:**
> It began doing that for me in 14.04 when compiz failed to reload correctly.

What a relief. I thought I might have a bad keyboard.

When I launched xscreensaver for the first time, I noticed that the app came with 10 min presets. This app has always
been a little buggy in that whenever I change a setting, like the 10 min presets, the app takes an unusually long time
to respond to user input and will crash if the user input is too fast. This made me think that the presets might be there
for package stability; so I changed them back to their original settings. Suddenly neither the app, nor the desktop crashed
anymore. That leaves me with two instabilities to reverify; but for now it appears that I have most of this licked. I'm going
to add those findings to the thread. It might take me a day or two to repost.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-03
It turns out that xscreensaver is still crashing; only it takes several hours instead of several minutes
for this to happen. After I replaced the rc file for cairo-clock, it held its position information in my
backup account; so I'm going to mark this thread as solved and concentrate on looking at xscreensaver
in isolation.

Thanks, Hannibal

---

