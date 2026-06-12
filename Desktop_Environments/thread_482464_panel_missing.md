---
title: "panel missing"
date: 2007-06-23
forum: Desktop Environments
---

### Post by keuphoria on 2007-06-23
hi, I have searched for this problem in the previous posts; but couldn't find one that will solve my problem.

I am using the xfce - ubuntu and both the top and bottom panels are missing in the desktop.

I have tried installing them(apt-get) but it says that it has already been installed. I have still gone ahead, and it says 0 installed, 0 updated, 44 unchanged.

what should I do now?

thank you very much

---

### Post by ugm6hr on 2007-06-23
Couple of options:
Try double-click from Thunar (/usr/bin/xfce4-panel)
Then Shut-down, and ensure the "Save session for future logins" is ticked.
Hopefully, the panels should appear when you boot back up again.

If that doesn't work, you can add xfce4-panel to start-up apps:
Applications->Settings->Autostarted Applications
Add
Name: Panel / Command: xfce4-panel &

This has been tried by someone else:
[http://ubuntuforums.org/showthread.php?t=467995&highlight=xfce4-panel](http://ubuntuforums.org/showthread.php?t=467995&highlight=xfce4-panel)

---

### Post by coffeeshawn on 2007-08-26
> **ugm6hr said:**
> Try double-click from Thunar (/usr/bin/xfce4-panel)
Then Shut-down, and ensure the "Save session for future logins" is ticked.
Hopefully, the panels should appear when you boot back up again.

I had the same problem, and this option worked for me.  Thanks ugm6hr!

---

### Post by formol on 2007-08-30
how to add panel to a second monitor

thank you

---

