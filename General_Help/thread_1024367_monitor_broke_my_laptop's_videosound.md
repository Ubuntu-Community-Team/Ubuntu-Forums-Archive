---
title: "monitor broke my laptop's video/sound"
date: 2008-12-28
forum: General Help
---

### Post by wall0645 on 2008-12-28
Hi, I plugged a monitor into my laptop to see if it worked, and opened the "Screens and Graphics" menu. I don't recall saving any new settings, but when I restarted, some bad stuff started happening:

The computer loads GRUB, does the Ubuntu loading screen (with fine graphics), then the loading stops at "running local boot scripts", where the screen flashes black a few times, then there's a bunch of weird jumbled colored lines, then a popup with the following message comes up:

"Ubuntu is running in low-graphics mode

Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself"

And you are given the option to Configure (Screens and Graphics menu), Shut Down, or Continue.

When I continue I have no sound, and the resolution is 800x600.

What happened? What should I do?

---

### Post by fitzbuntu on 2008-12-28
I'm no expert but a few things I would try:

open a console and do:

```
ls /etc/X11
```

If your settings have been altered in some way, usually a backup is made first which will be called something like 'xorg.conf_backup_200812290400'.

It's simply a matter of taking the last backup and restoring it (backup the current first just in case (you may need to use sudo):
```

cp -p xorg.conf xorg.conf.mybackup
cp -p xorg.conf_backup_200812290400 xorg.conf
```

Then just restart X (ctrl+alt+backspace).

If this doesn't work, or you don't have a backup, could it be you have NVidia/AMD graphics card and the driver needs to be installed/reactivated? I have an NVidia and I used to have to go to System -> Administration -> Hardware Drivers and check the box for the restricted driver after an upgrade.

Otherwise you'll need to edit the xorg.conf file directly but I think this has changed with Ibex.. someone else should be able to advise.:-k

---

### Post by wall0645 on 2008-12-29
I suppose it should be noted that my laptop is still on 8.04, not Intrepid.

Don't have NVidia/AMD graphics card either. Just have some onboard job, but don't know which kind. Suppose I should look into that...

---

### Post by fitzbuntu on 2008-12-29
Did you try locating a backup?

Otherwise have a look at this:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Look at the section at the bottom entitled _"Setting resolution changes in xorg.conf"_

You could also try an upgrade or reinstall of your distro.

---

