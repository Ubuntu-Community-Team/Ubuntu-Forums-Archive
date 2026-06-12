---
title: "Restart Behavior"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Emerzen on 2006-08-12
Obscure problem:

I have a Dell Dim. 8400 w/ an Intel 925X chipset.  When Dapper reboots my computer, I hear a click and the POST takes quite awhile.  When XP reboots, no click and it POSTs quickly.  Both OS's are on 1st drive partition 2 and 1 respectively.

Any ideas?

---

### Post by jchau on 2006-08-12
I don't think the BIOS can tell what OS it is booting to, so it probably due to the OS that shutdowns before the reboot.  To test this, you can try rebooting from win to ubuntu and vice versa.  Then try that again, but with a full shutdown in between (poweroff).  That should give you a better idea of what is happening.

Also, I have a Dell Latitiude D410 with the A05 version of the BIOS; the BIOS has a quick booting setting (forgot what it is really called), but it reverts to the slower one when the system fails to start properly on the previous startup.  Perhaps Ubuntu is causing your BIOS to think that it isn't starting properly.  

Another possiblilty is that the click is caused by some of your hardware (probably harddrive) powering off during the shutdown part of your reboot, causing your computer to need to turn on those devices again, consuming a bit of extra time.

---

### Post by Emerzen on 2006-08-13
After playing around w/ Win and Ubuntu, I think you're right about the harddrive powering off during a reboot.  Do you know of any way to prevent this?  Thanks for the reply, btw.

---

### Post by jchau on 2006-08-13
Sorry, I don't have any idea about how to solve this.  A google for the terms, "ubuntu hard-drive power off," seems to show people with the opposite problem.  However, it seems to suggest that some setting/module might be able to modify the behavior.  

Good luck!

---

### Post by Emerzen on 2006-08-13
Thanks, I'll give that a whirl.

---

