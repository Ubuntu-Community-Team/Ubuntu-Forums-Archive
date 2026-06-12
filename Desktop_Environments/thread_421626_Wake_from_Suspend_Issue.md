---
title: "Wake from Suspend Issue"
date: 2007-04-24
forum: Desktop Environments
---

### Post by RGCook on 2007-04-24
I have feisty 7.04 running fine on an Abit UL8 MB, 2GB Ram, ATI 9800 Radeon (R350 Driver), Canon N1220U scanner, Minolta 2400W Color laser, Beryl functioning with no problems. In fact alll of my hardware and software works great. Beryl is flawless and I no issues to report. None.

That said, when I put my computer to sleep, it does so quickly and wakes when I hit power button. However, after I enter my pw and Gnome reappears, nothing can be selected with the mouse. It's like Gnome is not receiving mouse clicks. Also, there is no affect from using the keyboard. I also see a pop-up appear after reawakening that says there was a problem putting the computer into sleep mode. Not sure what that problem is because going to sleep is not a problem, waking up is.

The only way out of this is to hard reset the machine. I normally leave my system on 100% of the time, but when I know it will not be needed for access or processing other tasks, it would be nice to have the suspend work. Any ideas on how to troubleshoot this would be appreciated.

Bob

---

### Post by crmccreary on 2007-04-28
I'm also having a wake from suspend issue with Feisty Fawn, although my desktop doesn't even wake up. When it gets suspended, waking never makes it to X much less to gdm. Here's a snippet from /var/log/messages:

---

### Post by smorar on 2007-04-28
To solve the mouse issue, in your BIOS, under the power management setup check if there is an option for waking up USB. If so, enable that, and your mouse (and other USB devices) should work on resume from S3 suspend.

---

### Post by talcite on 2007-04-29
I'm using beryl as well and the comp won't resume from suspend or hibernate either. I haven't had the chance to test with beryl off, but I have a PS2 keyboard  and it has no effect on the resume. X doesn't start. I get one icon where the mouse is, and I can move the mouse but nothing else happens.

---

### Post by pgilmon on 2007-05-01
The same happens to me when I try to hibernate with Beryl on. I'm using Feisty. Hibernating works right when Beryl is off. No USB keyboard or mouse.

---

