---
title: "How to add ubuntu9.04 to Windows 7 Boot Loader"
date: 2009-05-08
forum: General Help
---

### Post by ownsuall on 2009-05-08
I've installed Windows 7 on my computer and it took over my computer(like all winodws OS) and took out my Grub Boot loader so how do I make it so I can boot ubuntu again? Any help apricated

---

### Post by caljohnsmith on 2009-05-08
To reinstall Grub, you could follow these directions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you need help adding Windows 7 to your Grub menu, then how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by logos34 on 2009-05-08
cal beat me to it

---

