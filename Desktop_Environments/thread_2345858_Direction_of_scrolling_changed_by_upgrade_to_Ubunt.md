---
title: "Direction of scrolling changed by upgrade to Ubuntu GNOME 16.10"
date: 2016-12-08
forum: Desktop Environments
---

### Post by maf14129 on 2016-12-08
Hi,

I'm running Ubuntu GNOME 64 bit in a Virtualbox VM on a Windows 7 host. The upgrade from 16.04 to 16.10 has changed the scrolling direction in all windows. Toggling 'Settings > Mouse & Touchpad > Natural Scrolling' does nothing. I installed Ubuntu GNOME 16.10 in a new VM and found it behaves the same way.

What am I missing? How can I make the windows in Ubuntu 16.10 scroll the same way as all other windows on my computer do?

Thanks in advance,
maf14129

---

### Post by maf14129 on 2016-12-11
I have found an answer [here]("http://unix.stackexchange.com/questions/307928/how-to-disable-natural-scrolling") and and solved my problem with
```
$ gsettings set org.gnome.desktop.peripherals.touchpad natural-scroll false
```

---

