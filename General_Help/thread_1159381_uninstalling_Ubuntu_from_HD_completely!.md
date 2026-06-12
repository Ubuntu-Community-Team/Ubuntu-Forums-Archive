---
title: "uninstalling Ubuntu from HD completely!"
date: 2009-05-14
forum: General Help
---

### Post by Mister LinOx on 2009-05-14
Okay. My grandmother now has this PC, and she threw a bitch fit about linux saying it brought virii and crashed the power supply having an XP and Ubuntu dual boot and all of that Windows supporter junk. Plus, she says the guys at the hardware store said that.

   Anyway, I deleted the Ubuntu partition completely. That includes the /home partition and swap. Now when I restart(take not I a in the live CD), the grub still comes up saying error 22. So, I was thining that all I would have to do is open up the terminal and find the command to delete the grub menu from the area it's installed, but I figured my fellow "Linux-Mates" would be able to tell me if that's correct or not.

                            Thank you guys in advanced.

---

### Post by PupSpark on 2009-05-14
Try using fix in the windows install CD and typing "fixmbr". There was another one, too. It might have been fixboot.

---

### Post by Mister LinOx on 2009-05-14
> **PupSpark said:**
> Try using fix in the windows install CD and typing "fixmbr". There was another one, too. It might have been fixboot.

Okay. I'll go try this, then I'll come back to see if it worked.


still a little upset about uninstalling it though. Haha.

---

### Post by Mister LinOx on 2009-05-14
Okay. My grandmother popped in the recovery CD and boot from it. She selected to re-format the Hard Drive and we'll see how it goes. It's pretty funny how she was yelling at me saying I had no idea what I was talking about saying I ruined the whole computer and she needed this and that replace, a new hardrive(while the current one has around 150GB) and everything. Oh well. 

Thank you for helping me,but I might not be done if it still doesn't work. =P

---

### Post by PupSpark on 2009-05-15
Bummer. Do you think she would have had the same reaction if you had installed it on a serperate hard drive? 

Something similar happened to me: My family generally thinks of anything but Windows to be the computer devils, and that pisses me off so much(huge Linux supporter). They tried to persuade me to uninstall it from my computer. I told them no. I had previously tried a dual boot with my external hard drive on it, (Because of some BIOS issues on my new computer, I can't use it with it) and they said it made the computer slow... It's actually been running faster. They're all just convinced that windows is the only thing worth booting.

Sorry if I took it too far.

---

### Post by logos34 on 2009-05-15
> **Mister LinOx said:**
> Okay. My grandmother popped in the recovery CD and boot from it. She selected to re-format the Hard Drive and we'll see how it goes.

reformatting the drive was not necessary..all you had to do was press "R" for recovery console then type fixmbr (as mentioned previously) at the prompt to restore windows bootloader...Reformat means you lose everything on the windows partition(s) and must reinstall.  She's probably apoplectic by now..

> 
linux saying it brought virii and crashed the power supply having an XP and Ubuntu dual boot and all of that Windows supporter junk. Plus, she says the guys at the hardware store said that.

what b.s....especially the part about dual-boot being a power overload (hah)

---

