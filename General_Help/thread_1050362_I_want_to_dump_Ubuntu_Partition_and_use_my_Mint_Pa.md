---
title: "I want to dump Ubuntu Partition and use my Mint Partition as the only OS."
date: 2009-01-25
forum: General Help
---

### Post by archangel74 on 2009-01-25
Can someone tell me how to delete Ubuntu partition for my Mint partition.  I never use the Ubuntu and it's just a pain to log into once a month to update it.  What do I need to watch out for and will I need to move all the files on the Ubuntu side to the Mint side?

---

### Post by caljohnsmith on 2009-01-25
One thing to watch out for is if your Mint partition number will change when you delete the Ubuntu partition. In other words, if Ubuntu is on sda5 for example, then if you delete it, sda6 becomes sda5, sda7 becomes sda6, etc. That will affect whether you can boot or not if Mint is in charge of the booting process. If you have any problems booting after deleting the Ubuntu partition, just reinstall Grub via [these directions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and you should be fine. Good luck and let me know how it goes.

---

### Post by grndslm on 2009-01-25
no way, man.  why wouldn't mint be able to handle changing grub?

---

### Post by vegetarianshrimp on 2009-01-25
Gparted maybe? Or am I totally misunderstanding what you are saying?

---

