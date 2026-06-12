---
title: "compiz and ubuntu desktop settings reset on reboot"
date: 2009-09-12
forum: Desktop Environments
---

### Post by abhinav90 on 2009-09-12
i have installed compiz on my ubuntu machine which works on GNOME and with 9.04. Everytime my machine reboots my visual effects of GNOME get reset from "normal" to "no effects" additionally all my compiz settings go back to default. Why is this happening and can u pls help me solve this issue so that when i switch off and switch on my machine all my visual settings remain.

---

### Post by thug4702 on 2009-09-12
U  had this proplem b4 but now its working fine
 
i think there is a file that will be created to save compiz settings but this file is not on your system so i think you will have to search for it and create it or just do a system fix or restore

---

### Post by abhinav90 on 2009-09-12
can you guide me through the process of which file and where to create it to save compiz settings. Also how do i go about a system restore or fix.

---

### Post by abhinav90 on 2009-09-15
i simply need help with the fact that my machines, desktop effects get reset to 'none' upon every reboot. How do i make it saved at 'normal effects'

---

### Post by abhinav90 on 2009-09-16
bump

---

### Post by endlessmobius on 2010-01-12
I was just having this problem as well, except that I am using a custom Compiz configuration. I configured Compiz using ccsm, and then I had to install simple-ccsm to even get the Custom option to show up on the Visual Effects tab of the Gnome Appearance Preferences. Ultimately though, my problem was the same: the setting would return to None on every reboot.

For some reason, re-saving my Gnome session seemed to fix the problem. In System->Preferences->Startup Applications, on the Options tab, you can click the Remember Currently Running Applications button (I did this with no other applications running, as I did not want to run any extra startup programs).

After doing this, Compiz ran at startup. I think I may have saved my session (this same way) at some point in the past, with Metacity as my window manager, so Gnome continued to run Metacity on startup even after switching the preference to Compiz. I don't think this would have happened had I not saved my session previously.

My case may be a very specific one, but maybe this will work for you too.

---

### Post by yoppt on 2010-05-29
this worked like charm on mint 9

---

### Post by Subespaciovectorial on 2010-07-13
Thank you endlessmobius, it was exactly what I was looking for.

---

