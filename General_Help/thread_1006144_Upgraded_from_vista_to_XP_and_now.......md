---
title: "Upgraded from vista to XP and now......"
date: 2008-12-09
forum: General Help
---

### Post by skoalman88 on 2008-12-09
the grub menu is gone and I can't boot into ubuntu (gutsy. How can I get the menu back up?


Thanks.

---

### Post by HotShotDJ on 2008-12-09
Give this a try: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by abhilashm86 on 2008-12-09
> **skoalman88 said:**
> the grub menu is gone and I can't boot into ubuntu (gutsy. How can I get the menu back up?


Thanks.
haven't u made a backup of menu.lst,do it the next time,command is
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

hey if u can see the GRUB while boot up,press e to edit boot options,there u will get default ubuntu boot options,from there u correct menu.lst and press d,ubuntu will boot normally,but options in the menu.lst wil not be modified and saved so follow these steps to modify and save
sudo gedit /boot/grub/menu.lst

then from backup menu.lst correct the changes and save,gud luck
reply after u do,even i did 2 weeks back

---

