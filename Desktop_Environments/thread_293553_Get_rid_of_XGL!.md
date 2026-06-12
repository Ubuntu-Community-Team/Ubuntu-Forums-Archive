---
title: "Get rid of XGL!"
date: 2006-11-05
forum: Desktop Environments
---

### Post by martinrandau on 2006-11-05
I activated Desktop Effects in KDE and restarted the X-server. It wanted me to change the section "Extensions" from "0" to "Enabled". Now, I can't log in. The X-server crashes upon entering KDM. 

What is the way to, through config-files (I have no X, completely remove all signs of XGL and desktop effects? I just want to get it working again.

(I'm sorry it is so vague but I can't exactly remember the names)

---

### Post by TigerCR1200 on 2006-11-05
Press CTRL ALT F1 and it will take you to a command prompt. Open your xorg.conf file and change Enabled back to 0. That will disable it, if you still cant get back into X after that you can use the apt-get uninstall command to remove packages you want removed. "sudo apt-get uninstall pkgname"

---

### Post by martinrandau on 2006-11-05
ctrl-alt-F1 does not bring me to tty1. The screen is completely frozen. I can boot with the failsafe mode which brings me a command line. 

As for changing it to "0", this was the first thing I did and it didn't work.

Is there no way to simply remove everything that has to do with these desktop effects?

Thanks for any help.

---

### Post by TigerCR1200 on 2006-11-05
I am not that familar with KDE so bear with me or hope a KDE person shows up.

The desktop effects you enabled are part of KDE or a package you installed to run with KDE?

---

### Post by martinrandau on 2006-11-05
I guess they are a part of KDE as I found them under the apperance&themes section on kcontrol. I did not install any extra package.

---

### Post by TigerCR1200 on 2006-11-05
There should be some config files you could disable it in possibly in the /home/user/.apps/KDE ... I think that is the path.

---

### Post by martinrandau on 2006-11-05
No luck there. .apps/KDE didn't exist but I searched .kde and didn't find anything!

Wouldn't it just work by reinstalling xorg?

---

