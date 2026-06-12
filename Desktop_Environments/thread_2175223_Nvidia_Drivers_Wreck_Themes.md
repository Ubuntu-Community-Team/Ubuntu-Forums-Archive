---
title: "Nvidia Drivers Wreck Themes"
date: 2013-09-18
forum: Desktop Environments
---

### Post by Shibblet on 2013-09-18
Can anyone tell me what the heck is going on?

I install the Nvidia drivers in Xubuntu 13.04, and when I reboot, all of my themes are messed up, and I can't put them back to the way they were.

---

### Post by Shibblet on 2013-09-19
Bump.

---

### Post by stinkeye on 2013-09-19
Maybe explain "messed up".
Pic?

---

### Post by Toz on 2013-09-19
Maybe [this]("http://ubuntuforums.org/showthread.php?t=2077000")?

Agree with stinkeye. Without more info, we're just guessing.

---

### Post by Bastian_Cramer on 2013-10-02
Even if it is a little late, there is a solution.
I found the exact same error and themes/icons were
all messed up.

After installation of the nvidia drivers you have
to complete the configuration with nvidia-settings as root.
I recommend to create a [backup]("https://help.ubuntu.com/community/BackupYourSystem") before trying to change any important drivers or settings.


[LIST=1]
[*]Start the terminal (Alt+F2 and enter xterm and push run)
[*]Enter the command "gksu nvidia-settings" (without quotes) and press enter
[*]Enter your password and press ok
[*]NVIDIA X Server Settings opens
[*]Goto "X Server Display Configuration"
[*]Setup displays or leave as it is (not in the scope of this answer)
[*]Push the Button "Save to X Configuration File" (This is the important step which fixes the themes)
[*]Leave the path blank and push the "Save" button
[*]Logout and login again or reboot xubuntu
[/LIST]

I hope it helped.

---

