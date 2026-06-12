---
title: "Dual Monitor, second monitor goes blank"
date: 2010-04-03
forum: Desktop Environments
---

### Post by mstjohn1974 on 2010-04-03
Hello,

I am having trouble with my dual monitor set-up. the second monitor goes blank and is not coming back only if I shut-down and then boot up it is back. I turned off power management and screen saver. I am using a ATI Technologies Inc Mobility Radeon HD 3450, Monitor 2 is a Dell IM1910N and extends to Monitor 1 a Samsung SyncMaster 920nw. I am using the ATi /AMD proprietary FGLRX Driver that comes with Ubuntu 9.10. The Resolution on the Dell is 1366x768 (preferred) and on the SyncMaster it is 1440x900 (preferred). Is there a way to avoid the SyncMaster from going blank?

thanks

---

### Post by QIII on 2010-04-03
Are you using the Catalyst Control Center (AMD/ATI's graphical tool to compliment the driver) to set up your monitor configuration?

---

### Post by mstjohn1974 on 2010-04-03
Indeed, it's Version 2.11

---

### Post by QIII on 2010-04-08
Sorry for long wait.

In Karmic, you should be using Catalyst Control Center 9.10 (easy to remember here, since Karmic is 9.10)

Just be prepared if you update to Lucid...  The driver you are using now and CCC 9.10 will not work with the new Xserver.

---

### Post by mstjohn1974 on 2010-04-08
I think i am wrong regarding the installed package version...I looked at apt-get and it is version 2:8.660-0ubuntu4 (Karmic) how do you get version 9.10?

---

### Post by QIII on 2010-04-08
You have the right driver.

Search synaptic for fglrx-amdcccle to get Catalyst 9.10 so you can use a graphical tool to set up your screens.

---

### Post by mstjohn1974 on 2010-04-09
well, I now have the latest and greatest and still experiencing the Monitor to stays off after Powermanagement kicks in. I have to reboot the box to get both screens on. I also cannot turn the monitors off at all. when i do that i have the same issue. after reboot it is okay as long as i am not turning off the monitors or turn on the power management. Any further ideas? It appears like the Video Card turns off the second VGA Head on the card when it cannot detect the screen and only the reboot brings it back.

thanks for any help

---

### Post by QIII on 2010-04-09
I'm going to have to do some research when I get home.

Unfortunately, I don't have any machines running Karmic any longer.  But I've never experienced this issue before, even with three monitors.

Right now I have two on one of my machines and everything works fine in Lucid.

---

### Post by mstjohn1974 on 2010-04-09
Thanks anyways... I think I am going to try a Nvidia GeForce 8400GS 

thanks a lot for the effort...I appreciate this

---

