---
title: "removing ubuntu"
date: 2008-12-26
forum: General Help
---

### Post by terry_gardener on 2008-12-26
i currently have dual boot system default linpus lite and ubuntu 8.10.

is there an easy way to remove ubuntu from the system a have just linpus on it without wiping out the linpus OS.

i was just thinking of just booting into ubuntu liveusb and then using gparted to remove the ubuntu partition and resizing the linpus one to full size, the only problem i can think of is grub, how to i restore grub to the original configuration.

this is one the acer aspire one netbook 

any ideas

Thanks

---

### Post by tuxxy on 2008-12-26
You have the correct method the only issue you may have is GRUB as you say and it is fairly simple to restore just follow the steps in [this guide]("http://ubuntuforums.org/showthread.php?t=224351") :)

---

### Post by terry_gardener on 2008-12-26
i have deleted the ubuntu partition and then resized the linpus partition to full size revooted got grub error 22, then wen through the the steps in the link you provided and now when i try and boot just get blank screen nothing else happens. 

any further ideas 

thanks

---

### Post by bodhi.zazen on 2008-12-26
You will need to restore grub.

Like this :

        [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

