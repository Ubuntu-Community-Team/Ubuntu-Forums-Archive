---
title: "System stops responding after login for 1min"
date: 2012-05-18
forum: Desktop Environments
---

### Post by tommo1982 on 2012-05-18
Hi,

I have a problem I'm not quite sure how to fix. I asked for help on #xubuntu IRC channel and was suggested to use bootchart to log the boot process. I finally got the png file where the system stops for 1min. Okay, some explanation. Everything is going nicely, login screen pops up, I type my password press Enter and ... nothing. The only thing visible is mouse cursor and default wallpaper. I can change between the consoles with ALT+CTRL+F1, so the system responds, but I have to wait about 1min for the system to fully load desktop. As I mentioned, I have the png file but I don't know how to read it. Can someone take a look and see if there's anything out of the ordinary?

---

### Post by 2F4U on 2012-05-18
I would look into the autostarted applications. Sounds to me as something is starting right after the login. Another possibility that comes to my mind is that you, intensionally or not, left a program running upon shutdown or logout and the program is restarted because the session was saved.

---

### Post by tommo1982 on 2012-05-18
I checked the autostart and there's nothing that could cause this. Things that were added by me are Guake and DesktopNova, but they start with the desktop. I also turned off sessions saving.

---

### Post by rai4shu2 on 2012-05-18
This problem is reported rather frequently:

see: [http://ubuntuforums.org/showpost.php?p=11918449&postcount=15](http://ubuntuforums.org/showpost.php?p=11918449&postcount=15)

---

### Post by tommo1982 on 2012-05-18
Thank you *rai4shu2*. At least I know I didn't cause the problem, heh. Going to wait for the fix.

Marked as Solved. Hope it helps others to find what they are looking for.

---

