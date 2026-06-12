---
title: "Auto Mounting HDDs"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by money2themax on 2007-12-03
I want to auto mount my Samsung 200GB HDD when i login it in NTFS that was formatted by Windows XP MCE how do i have it auto mount when i log in?

---

### Post by FuturePilot on 2007-12-03
Have you installed the ntfs-config package?
```
sudo apt-get install ntfs-config
```
Then you can configure access to the drive and it should mount automatically when you login

---

### Post by money2themax on 2007-12-03
i can read run write the whole nine yards

---

### Post by FuturePilot on 2007-12-03
Hi :)
It's still not mounting automatically? Did you use ntfs-config to create a mount point?

---

### Post by money2themax on 2007-12-03
it worked how do i check if it worked thru terminal?

also it deleted something [like a system file] i noticed i'm just worried that it might mess up my HDD cuz my personal stuff is on there

---

