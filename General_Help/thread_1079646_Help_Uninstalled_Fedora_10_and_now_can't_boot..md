---
title: "Help: Uninstalled Fedora 10 and now can't boot."
date: 2009-02-24
forum: General Help
---

### Post by StratTele on 2009-02-24
I installed Fedora 10 KDE the other day to see if I liked it. I installed it as a seperate partition along with my WindowsXP and Ubuntu. After a little while I realized I didn't need the switch from Ubuntu. I used GParted and removed the fedora partion and a partition that was named "boot" which was not there before I installed Fedora. I'm assuming that right there is the cause of my problem -_-. Anyway, the original boot menu that appeared before my Fedora escapade does not appear anymore. Instead this shows up:


[Minimal BASH - Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible completions at a device/filename.]

grub>_


I have no clue what to do. I'm running off the Ubuntu disk right now and I see that my two drives are still there and I can access my Ubuntu partition. If anyone can give me a way to retrieve my old boot menu or a command to boot from grub that would be greatly appreciated.

Thank you in advance for any and all help.

---

### Post by taurus on 2009-02-24
Sounds like you need to reinstall GRUB to MBR so you can boot Ubuntu and windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by StratTele on 2009-02-24
<3<3<3 Thank you so much, worked perfectly!

---

