---
title: "Why does zenity | losetup not work in post login script?"
date: 2011-04-05
forum: Desktop Environments
---

### Post by MichiGreat on 2011-04-05
**Hello!**

I put the following lines of code in /etc/gdm/PostLogin/Default:

LOOPDEV=`losetup -f`
zenity --title "Willkommen!" --entry --hide-text --text "Willkommen am Eee PC 1005HA von Michael Kremser." | losetup -e AES128 -p0 $LOOPDEV /dev/sda7
zenity --info --text="`losetup -a`"
mount $LOOPDEV /home
zenity --info --text="`mount | tail -2`"

When I log in, the dialogs are shown and I can enter the password. But losetup then does obviously nothing, because the line that prints the output of "losetup -a" shows an empty message. I even tried to redirect losetup's output to a file, but the file remained empty.

If I execute the script from gnome-terminal after log in, it works perfectly.

Any ideas of what goes wrong here?

Best regards

*Michael*

EDIT: Yet another tip from [http://dx4.org/security/partitionencryption.html](http://dx4.org/security/partitionencryption.html) is using "/usr/bin/aterm -e /usr/local/bin/mounthome", but that also doesn't work in my case. The window from aterm shortly appears and then disappears.

---

