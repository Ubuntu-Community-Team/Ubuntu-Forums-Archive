---
title: "Change /boot partition without reinstalling?"
date: 2009-02-14
forum: General Help
---

### Post by Daeluin on 2009-02-14
So I made a separate boot partition, and somehow it's only 54 megs. Only about enough for 2 kernel images and update-manager is always screaming at me to fix it. 

Is it possible to bring this back to my root partition, toggle the bootable flag on the root partition without overwriting any data, copy the files over, make the right changes in fstab, and then somehow have grub update itself for the new pathing? 

Seems like it should be, but it's not something I'm going to try without knowing for sure... thanks for any suggestions!

---

### Post by caljohnsmith on 2009-02-14
Yes, you should be able to integrate your boot partition back into your root partition. I think it would help to first get more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

