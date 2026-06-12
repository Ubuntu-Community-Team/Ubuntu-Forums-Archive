---
title: "Black screen after changing desktop preferences"
date: 2009-05-20
forum: Desktop Environments
---

### Post by raz230 on 2009-05-20
Hello,

I am using Kubuntu 9.04 KDE 4 w/ATI video card using restricted drivers.

I was looking for the hotkey that lets you toggle between your desktops and I was in System Settings > Desktop under effects.  I changed the desktop changer effect from "Slide" to "Cube" and when I hit Apply my desktop went black.  I tried to restart the X server with CTRL ALT BCKSPC but I had to reboot.  

Rebooting did not help.  I booted to Grub and went to recovery mode and chose the option to auto-repair graphics problems. That also did nothing.

Please don't tell me I have to re-install because of changing one option :)

Is there a way to reset the whatever back to how I had it so I can use my computer?  I presume I can boot to shell and do some stuff there but I don't know what I did.

Any help is appreciated.

raz

---

### Post by Happy_Man on 2009-05-20
You can always install something light like fluxbox from a terminal (use alt-F3 to get to one), and then use that to open the system settings and change the effect back.

---

### Post by raz230 on 2009-05-20
I wish it was that easy.
When my system boots it all appears normal.  I get the kubuntu progress bar and then when I see my desktop, it's black with some smeared video lines near the top.  I have no mouse.  The video appears to toggle - it goes full on black, then back to the first part with the "smear"  It does this sometimes.  Not always.

I cannot open a shell prompt.  Well, maybe I am.  I can't see it.

I have to boot to recovery where I can only login as root.

I removed my .kde/.... kwinrc file and rebooted.  I tried setting the compositing to false as some other postes suggested.

I can't beleive changing one option via the system settings could cause such a disaster!  This computer is litterally brand new.

Everything I've researched suggested xorg.cong or ~/.kde.../kwinrc was the problem.  I've tried both and neither worked.

At the shell prompt, when I get to the root login (which I enabled the other day before this happened) I can go 'startx' under root and the same thing happens.  

I've looked in the logs under /var/log/syslog and I see 

Failed to start x server and various x server messages but nothing really helpful.

I guess I will have to rebuild.  yay

---

### Post by raz230 on 2009-05-20
YIPPY!  I fixed it.

I realized after my last post that since the problem happened to the root user also that the problem was not located in my home folder- so it had t be the xorg.conf file

Previously I renamed it to .old but I didn't notice a new one getting generated.

I went to 

/etc/X11 and "ls"'d the folder.  I noted some xorg.conf.YYYYMMDDHHMMSS files from today- before my problem began.

I mv'd my xorg.conf file to a .old file and cp's the earliest previous copy of the other xorg files to xorg.conf, did a reboot and I'm back.

Now, do you think the syslog could have had a more helpful error message, or even better, KDE should not show me options that are not safe to use?

Anyway, it's better now

---

### Post by mattchenzo on 2009-08-07
man, i hate to sound retarded, but i did the same thing as you, and dont exactly know how to do what you said to do to fix it...
i am reading up on everything i can, but trying to learn how to do this stuff takes some time, and i was hoping not to have to keep using vista for too long...

dumb-dumb instructions please???


:(

---

### Post by Happy_Man on 2009-08-09
> **mattchenzo said:**
> man, i hate to sound retarded, but i did the same thing as you, and dont exactly know how to do what you said to do to fix it...
i am reading up on everything i can, but trying to learn how to do this stuff takes some time, and i was hoping not to have to keep using vista for too long...

dumb-dumb instructions please???


:(
All OP did was restore a backup. Here, just copy and paste this into your terminal, one line at a time, and you'll be golden.

```
cd /etc/X11
ls

```

Here, note the exact name of a backup xorg.conf (it'll be in the format xorg.conf.YYYYMMDDHHMMSS) from when you know your system was working. Try to choose the most recent backup you remember working. Copy it down.

```
mv xorg.conf xorg.conf.old
cp xorg.conf.YYYYMMDDHHMMSS xorg.conf
```

Reboot. See if that works.

---

