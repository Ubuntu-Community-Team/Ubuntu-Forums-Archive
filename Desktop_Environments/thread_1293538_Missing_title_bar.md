---
title: "Missing title bar"
date: 2009-10-17
forum: Desktop Environments
---

### Post by xfso1 on 2009-10-17
Hello, so the problem is: I messed with the usr/share/themes folder and it's gone (I have no idea how) and after a restart my title bar is missing on all windows. I placed a new themes folder with a few themes I downloaded but it didn't help... and I searched for help but everything I find is related to compiz which I never installed.  If you have any idea on how to fix this and restore default themes folder I'd really appreciate it.

---

### Post by gnuvistawouldbecool on 2009-10-17
Try running the command metacity --replace in a terminal.

While you may not have installed compiz, it might be there by default anyway in Xubuntu (not sure on that).  The above command would then ensure you aren't running compiz at least.

If you changed something in the themes, go into appearance preferences and change the theme you are using, or download a different one.

---

### Post by xfso1 on 2009-10-17
I get: The program 'metacity' is currently not installed.  

and as I said, I accidentally deleted the themes folder, and already downloaded other themes (not default ones) but still no title bar. 

If you want I can post a screenshot...

---

### Post by frankwakeman on 2009-10-17
Xubuntu uses xfwm rather than metacity anyway.  I'm no master and am prone to the 'use a tank to swat a fly' methods, but I would go into Synaptic and reinstall xfwm (or it might be xfwm4) first, maybe that'd put all the settings back to normal.

Or I'd get the live CD and paste the missing folder back in.

If you reboot and choose the second bootloader option (repair or something like that), is there any difference?

If someone with better beans replies before I click send, ignore me!

---

### Post by xfso1 on 2009-10-17
I did a reinstall to xfwm4 from Synaptic, and it worked! the title bar is back!

Thanks a lot!:)

---

### Post by abdusamed on 2009-10-17
if u recently installed the os.. the best shot is simple reintalling the os.. i think u probably somehow messed up the who OS! i did that quite often.. simply reinstalled it!!

---

### Post by frankwakeman on 2009-10-17
Excellent.  I'm seldom of any use to anyone! :P

---

