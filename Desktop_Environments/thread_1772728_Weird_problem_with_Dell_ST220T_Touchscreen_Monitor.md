---
title: "Weird problem with Dell ST220T Touchscreen Monitor"
date: 2011-06-01
forum: Desktop Environments
---

### Post by luckymurari on 2011-06-01
I recently got hold of a Dell ST2220T touchscreen monitor. Initially when I installed Natty, multitouch worked out of box. But once I shut down the computer and boot again the touch itself stops working.


Even weird thing is this :

If I go to windows and restart the system (warm boot) to come back to Ubuntu, it works. After that if I restart (warm boot) Ubuntu , the touch works. But when I "shutdown" (cold boot) the computer, and start it again, it stops working. Only when I go back to windows and "restart" the system touch works.

This behaviour has been consistent. I searched the net and found out that when "warm boot" happens there are still some contents left in the memory. SO, I am thinking that the windows driver support is getting it to work in Ubuntu. 


But, I am not sure how to solve this. Can anyone help with regards to this please?

---

### Post by luckymurari on 2011-06-02
Can any one please help with this?

---

### Post by luckymurari on 2011-06-06
No one can help in this?

---

### Post by Copper Bezel on 2011-06-06
It's more likely that Windows is waking up the *controller* for the touchscreen on the hardware side, allowing Ubuntu to recognize it and load the appropriate driver, to my limited understanding of these things. No part of the Windows driver is going to be in memory, but if there's effectively a hardware switch that turns the touchscreen on, *that* could persist over a reboot.

I don't have any experience with touchscreens, however. You can find out specifics on whether it's being recognized and where it's connecting using gnome-device-manager (available in the repositories) but I wouldn't know how exactly to "wake it up", likely via a bash command.

---

### Post by luckymurari on 2011-06-07
> **Copper Bezel said:**
> It's more likely that Windows is waking up the *controller* for the touchscreen on the hardware side, allowing Ubuntu to recognize it and load the appropriate driver, to my limited understanding of these things. No part of the Windows driver is going to be in memory, but if there's effectively a hardware switch that turns the touchscreen on, *that* could persist over a reboot.

I don't have any experience with touchscreens, however. You can find out specifics on whether it's being recognized and where it's connecting using gnome-device-manager (available in the repositories) but I wouldn't know how exactly to "wake it up", likely via a bash command.

The device is apparently getting connected. But I have not gone any more forward with this.. ANy more pointers please :(

---

### Post by HughR on 2012-10-29
There's a new thread at [http://ubuntuforums.org/showthread.php?p=12181989]("http://ubuntuforums.org/showthread.php?p=12181989")

---

### Post by wildmanne39 on 2012-10-29
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

