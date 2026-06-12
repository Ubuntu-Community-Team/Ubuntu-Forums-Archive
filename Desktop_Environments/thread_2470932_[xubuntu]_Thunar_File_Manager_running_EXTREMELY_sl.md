---
title: "[xubuntu] Thunar File Manager running EXTREMELY slowly and crashing"
date: 2022-01-17
forum: Desktop Environments
---

### Post by RangerK on 2022-01-17
Hello everyone.

Can anyone give me some troubleshooting advice?

I've used Xubuntu for years and love it.  A few weeks ago, my filemanager Thunar (1.8.14) is lagging and crashing.

For example, it can take 30 seconds to open a folder, and sometime when I try to close the folder, I get the message:

> Warning

This window might be busy and is not responding. Do you want to terminate the application?

<folder name> - File Manager

I had the idea of trying to re-install Thunar.  So I went into SOFTWARE, and found Thunar and INSTALLED,   But when I click remove and then "ok", nothing further happens.

Any advice?

---

### Post by RangerK on 2022-01-17
ps - 

I tried *sudo apt remove thunar *followed by *sudo apt install thunar*, but the problems persist.

---

### Post by &amp;KyT$0P# on 2022-01-17
Can you check if this also happens in other file managers, e.g. PCManFM or Dolphin?

---

### Post by Holger_Gehrke on 2022-01-17
Thunar has no separate configuration files, it's settings and options are stored in xfconf and you can access them graphically with xfce4-settings-editor. You might want to take a look whether there's something wrong in there.

The last time Thunar was misbehaving on my system the actual culprit was not Thunar at all, it was the thumbnailing service tumbler which was called by Thunar and tried to make thumbnail images for some rather big video files ... A few changes to /etc/xdg/tumbler/tumbler.rc ended that problem.

Holger

---

