---
title: "Pangolin x64 desktop crashed after full update"
date: 2012-04-28
forum: Desktop Environments
---

### Post by sirrain on 2012-04-28
Hi everyone! i got a prompt about a video card issue (forgot the exact words) right after a complete update to my new pangolin x64 desktop wherein i had installed an amd radeon driver (amd-driver-installer-x86_64.run) just before the said update. after restarting, a selection box appears and any selection exits to a console where i have abs no idea what to do.. any help?

---

### Post by RJARRRPCGP on 2012-04-28
Did you do an upgrade installation from a previous Ubuntu?

---

### Post by tomatoe on 2012-04-28
Try this 
```
sudo apt-get purge xserver-xorg
 sudo apt-get install xserver-xorg xserver-xorg-video-all
 sudo reboot
```

---

