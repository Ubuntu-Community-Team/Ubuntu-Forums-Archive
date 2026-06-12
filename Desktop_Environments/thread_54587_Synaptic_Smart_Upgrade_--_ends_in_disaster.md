---
title: "Synaptic Smart Upgrade -- ends in disaster"
date: 2005-08-05
forum: Desktop Environments
---

### Post by j.hill on 2005-08-05
I installed Ubuntu about two weeks ago (computer specs below, in case it's relevant) and put xfce over it as a window manager.  Everything was working great.  It was a time of joy.

last night I downloaded Wine, about which I had been hearing good things, and installed it.  

I was already too tired to play around with Wine, but I figured I'd do a "smart upgrade" in Synaptic, since it's constantly warning me about how quickly packages go out of date.  

When I saw how long the upgrade was going to take, I went to bed and let it do its thing.

When I got up, the computer was asking me questions about my configuration.  The help screen suggested that I should choose the option "no configuration" if I wanted no changes to my configuration, so that's what I did.

There was also a question about my mail handling, which I forget, and I told the computer to do nothing since my mail had been working fine.

There may have been a third question, but I forget.

Then I got a couple of error messages about upgrades that had failed, but I couldn't decipher them.

The first sign of trouble was that Evolution had disappeared from the main menu.  So I fiddled around, and discovered that Evolution was still on the computer; only the menu seemed to be affected.  So I looked here and there, and thought I had figured out how to put Evolution back in the menu....only it didn't work.  So I restarted xfce to see whether the change took effect at that point.  It didn't.  So I rebooted the computer.

That's when the real trouble started.  At the login screen, I got an error message about the "default theme" from Ubuntu, and a different theme for the login.  And no keyboard function.  So I can't log in to Ubuntu.  The mouse still works, so I can choose the "failsafe GNOME" and "failsafe terminal" options on the login menu, but neither of those options actually does anything.  But I know the keyboard does actually work, since (1) I used it in Grub to select my OS; (2) I'm using it now in Windows to type this message.

This would all be easier to bear if I could get back into Ubuntu and try to find a history of what happened, so I could know what to fix.  But I can't.    My computer has been possessed by the ghost of Kafka.

Advice or magical intervention gratefully accepted.


Computer specs:

Athlon 2000XP processor
ASUS A7N266 VM/LAN/AA Motherboard
768 PC2700 RAM
Western Digital 80GB Hard Disk (for Windows)
Seagate 120 GB hard disk (for Ubuntu)
nVidia 32MB AGP Video
Dolby 5.1 Integrated Audio w/ SPDIF
nVidia 10/100 Integrated Ethernet

---

### Post by heimo on 2005-08-05
USB keyboard? Do you have several kernels to choose from in GRUB menu? (try older) There may be a way to make it work from Live CD - but it could be just easier to make backups that way and reinstall. If you can get keyboard working, it'll be a lot easier, so if you have PS/2 port and keyboard available... I'd try that.

After you get keyboard working, you should check that packages are fully installed (not "pending" unconfigured). I'd probably just 

 ```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade

```

---

