---
title: "Cannot find GRLDR, No WUBILDR."
date: 2009-05-07
forum: General Help
---

### Post by JamesDoe on 2009-05-07
Ok, so i am relatively new to ubuntu. So far everything has worked fine, aside from my own USER errors. Well recently i updated to 9.04, and got my wireless working again, and everything was fine. 2 nights ago i had irssi open in Terminal, 3 tabs in firefox, and Pidgin, i was opening a tab for Playlist.com when my cpu action light went solid on my computer and it completely froze up, would not respond to alt+ctrl+del or a single press of the power button. i held the button down and forced a system shutdown. Upon restart the following was outputted. 
```
Try(hd0,0):FAT32:NO WUBILDR
Try(hd0,1):NTFS5:no wubildr
Try(hd0,2):Invalid or Null
Try(hd0,3):Invalid or Null
Error:Cannot find GRLDR in all devices
```
i am typing this as i am running on a Live USB of Mint Linux. Any help is GREATLY appreciated.

---

### Post by JamesDoe on 2009-05-07
self bump. i could really use some help with this.
My WUBI loader has gone wrong, i need to know how to fix it, OR backup all data and settings and reinstall as a true dual boot and restore settings.

---

### Post by JamesDoe on 2009-05-09
bump again, any help guys/girls?

---

### Post by caljohnsmith on 2009-05-09
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by JamesDoe on 2009-05-09
I can't boot into Ubuntu, so I am currently putting Netbook Remix on my USB to install.

---

