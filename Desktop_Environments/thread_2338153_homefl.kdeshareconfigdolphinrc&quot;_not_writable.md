---
title: "/home/fl/.kde/share/config/dolphinrc&quot; not writable"
date: 2016-09-25
forum: Desktop Environments
---

### Post by francois.e on 2016-09-25
I have this problem of dolphin that did not want to open with this dialog box:/home/fl/.kde/share/config/dolphinrc" not writableI have changed permission of the file:sudo chmod +x ~/.kde/share/config/dolphinrcNow dolphin will open. However, there is still that and obsolete dialog box poping that I have so cancel before having access to dolphin:/home/fl/.kde/share/config/dolphinrc" not writableHere is an interesting output:https://ubuntuforums.org/showthread.php?t=1653045fl@fl-Satellite-Z930:~$ ps -fe|fgrep dolphin|fgrep -v fgrepfl        3192  1521  0 07:16 ?        00:00:00 /usr/bin/dolphin --icon system-file-manager -caption Dolphinfl        3195  3192  0 07:16 ?        00:00:00 /usr/bin/kdialog --title dolphin --msgbox Configuration file "/home/fl/.kde/share/config/dolphinrc" not writable. Please contact your system administrator.fl        3213  1521  0 07:17 ?        00:00:00 /usr/bin/dolphin --icon system-file-manager -caption Dolphinfl        3215  3213  0 07:17 ?        00:00:00 /usr/bin/kdialog --title dolphin --msgbox Configuration file "/home/fl/.kde/share/config/dolphinrc" not writable. Please contact your system administrator.fl@fl-Satellite-Z930:~$ Any ideas.

---

### Post by ajgreeny on 2016-09-25
Please repost or edit your post but this time with some formatting and punctuation to make it readable.

At present it is just a wall of text with no separate lines and is totally incomprehensible.
Please use **Code-Tags** for terminal output which I suspect is what some of the post is showing. See my signature below for a **How-to**

---

