---
title: "Manually start screensaver?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by jessexoc on 2006-08-30
Is there a way to manually start the screensaver in gnome? ie so that i could open a launcher and it would start straight away?

-Cheers

---

### Post by Cable on 2006-08-30
You could press Ctrl+Alt+L.  That's the keyboard shortcut to lock the screen.  You'll just have to type your password in to get back to your desktop.

---

### Post by jessexoc on 2006-08-30
What about starting the screensaver without locking the screen?

---

### Post by lynxus on 2006-08-30
what about creating a new shortcut / run for the app "gnome-screensaver"
or xscreensaver if thats installed ?

---

### Post by kaamos on 2006-08-30
Use a launcher with:

```
gnome-screensaver-command --activate
```

---

### Post by eladamri on 2006-09-04
Thank you, Kaamos.

---

### Post by bobby_d on 2008-01-30
Hi all,
Thanks for info - finally got it working.. Using Dapper 6.06.2 persistent (from USB) and I had a slight problem - running gnome-screensaver-command as root user from terminal gave

> gnome-screensaver-Message: Failed to connect to the D-BUS daemon: No reply within specified time

whereas ran as ubuntu user, it ran fine ??!! So, I tried as per: 

'Help running a terminal command from panel launcher'
[http://ubuntuforums.org/showthread.php?t=230275](http://ubuntuforums.org/showthread.php?t=230275)

and put the gnome-screensaver-command in a bash script, and then, as per
'run as different user'
[http://ubuntuforums.org/showthread.php?t=324202](http://ubuntuforums.org/showthread.php?t=324202)

calling in the launcher

> sudo su ubuntu screensaver-script

and then it started working for me...

Cheers

---

### Post by simplebeep on 2008-06-07
```
gnome-screensaver-command --activate
```

This worked for me.  Just be sure the launcher is set as an Application (not in terminal).

Thanks Kaamos!

---

