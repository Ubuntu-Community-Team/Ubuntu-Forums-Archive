---
title: "Steamwebhelper error after Apparmor updates"
date: 2024-07-14
forum: Gaming &amp; Leisure
---

### Post by keshara283 on 2024-07-14
Hi everyone,

Version: Ubuntu 24.04

I'm currently having an issue where when attempting to launch Steam (Flatpak), I'm getting the following "steamwebhelper, a critical Steam component, is not responding."

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293971&stc=1[/IMG]

I've tried each of the options in the window, and get same results on each attempt. I also noticed that this issue only occurred after updating my system where Apparmor took the bulk of my updates. This is unfortunately an area I know almost nothing about, and can't find too much online when attempting to research this issue.

I've also tried uninstalling and reinstalling the Steam Flatpak. I haven't tried running the .deb yet, but would prefer to keep the Flatpak instead if possible.

Does anyone have any clues as to what's going wrong, or even better a potential fix?

Thanks in advance :)

---

### Post by pinkysbrain on 2024-07-16
Just googling for the same thing and this seems to be the relevant bug :
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2072811](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2072811)

The hacky solution of deleting bwrap-userns-restrict and restarting worked.

---

### Post by Bashing-om on 2024-07-16
A fix for FlatPak is released:
Ubuntu Fast-Tracks AppArmor Fix for Flatpak Apps Failing to Start
[https://www.omgubuntu.co.uk/2024/07/ubuntu-apparmor-fix-for-telegram-flatpak](https://www.omgubuntu.co.uk/2024/07/ubuntu-apparmor-fix-for-telegram-flatpak)

-good work maintenance team :D -

---

### Post by currentshaft on 2024-07-16
Quite amazing this got past integration testing and quality assurance. Steam appears to be in the top 10 Flatpaks, yet no one even bothered to see if it launches with the deployed changes. I don't know about other users, but this has me questioning the integrity of Flatpak applications.

---

