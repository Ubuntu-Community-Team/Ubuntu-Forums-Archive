---
title: "Vanilla GNOME Boot Problem"
date: 2019-10-26
forum: Desktop Environments
---

### Post by virginius on 2019-10-26
I downloaded mini.iso from [here]("http://archive.ubuntu.com/ubuntu/dists/eoan/main/installer-amd64/current/images/netboot/") and installed Ubuntu without any DE. Then I installed GNOME using this command [I][SIZE=2][FONT=georgia][SIZE=2][FONT=arial]sudo apt install gnome-core.[/FONT][/SIZE]

[/FONT][/SIZE][/I]Now I have a clean, fast vanilla GNOME and it works flawlessly. The only problem is it doesn't boot properly. Sometimes it boots and and sometimes it gets stuck in a blank screen. Also Ubuntu logo doesn't appear during the boot, login screen or during the shutdown.


I had previously installed Ubuntu's GNOME using[SIZE=2]*[FONT=georgia] [FONT=arial]sudo apt install ubuntu-gnome-desktop[/FONT][/FONT]*[/SIZE] and there was no such issue. So what am I doing wrong here?

---

### Post by cruzer001 on 2019-10-28
Are you running the proper video driver?

Gnome-core does not come with the pretty boot screen, it must be added.

---

### Post by virginius on 2019-10-31
> **cruzer001 said:**
> Are you running the proper video driver?

Gnome-core does not come with the pretty boot screen, it must be added.

What is the package name for Ubuntu boot screen?

---

### Post by rbmorse on 2019-10-31
I have the same issue here with a stock install of 19.10 full distro. Using the Nvidia proprietary driver.  

If the stall happens, it usually happens on the first boot of the day.  Sometimes it stays stalled, sometimes it eventually loads a desktop but the GNOME setup will be incomplete, sometimes it comes fully up.  Generally, logging my user out and back in gets things going properly.

---

