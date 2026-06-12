---
title: "Grub problem after updating Windows XP"
date: 2008-12-25
forum: General Help
---

### Post by dosh on 2008-12-25
I am having a problem booting from Grub into Windows XP after updating Windows XP. I have a partitioned hard-drive with Ubuntu and Windows XP with Grub working well until I updated XP now when I select XP it just restarts even if I boot to Safe mode it needs to restart and it restarts Again. It shows the Windows XP starting screen with the dots going across and then after that finishes it just restarts. Any help much appreciated.

---

### Post by caljohnsmith on 2008-12-25
It sounds most likely that you have a Windows problem and not a Grub problem at this point, but in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully give us some idea what your problem might be.

---

