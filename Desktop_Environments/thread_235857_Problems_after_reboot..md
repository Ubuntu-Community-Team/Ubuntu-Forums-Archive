---
title: "Problems after reboot."
date: 2006-08-13
forum: Desktop Environments
---

### Post by Farbi on 2006-08-13
Hello I am fairly new to Ubuntu.  I've been at it for about 8 months.  The short story here is that My Motherboard shot sparks at me (like physically shot sparks(motherboard) and flame(powersupply) on a restart about 4 months ago.  The problem was a physical one and had nothing to do with Ubuntu (though I'm eyeing XP :~)  )   Anyway I finally got a new  (used) motherboard /proc and figured out why ubuntu wouldn't load (IDE channel 1 was shot and therefor the HD was listed as HDC not HDA. At least that's how I think it works...)  Either way if I use a liveCD and mount /dev/hdc2 (<-- linux partition) and edit /boot/grub/device.map & /boot/grub/menu.lst & /etc/fstab to reflect the change (hda--> hdc)  it boot fine into the ubuntu that I know and love.  However, when I restart it defaults back to hda.  I know that I am missing something somewhere... I just don't know what.  I searched the forums as much as I could to no avail... If anyone can help I would be happy to try anything you recommend (short of reinstalling, I have about 50gb music and about 75gb home movies that I have no way of backing up).   


Thanks in advance
Potiphar

---

