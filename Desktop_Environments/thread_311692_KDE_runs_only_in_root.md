---
title: "KDE runs only in root"
date: 2006-12-03
forum: Desktop Environments
---

### Post by Kivipallur on 2006-12-03
I have ubuntu installed and I wanted to try KDE.
I beleave "sudo aptitude install kubuntu-desktop" would be the right command.
Installation finished. Logged out. Choosed KDE session and logged in.
But the machine hangs and I see only a blue screen.
For some reason i tried to log in with root and there were no problems.
Then I tryed to run some KDE applications in gnome, none of them started. But if I used sudo then again everyting worked.

Any ideas why can I run KDE only in root?

---

### Post by pay on 2006-12-03
Try ```
sudo chmod 777 -R /home/YOUR_USER_NAME
```

---

### Post by Kivipallur on 2006-12-03
Thank you, that helped.
At first it said that the home folder should not be writable to others but user must have all rights and the $HOME/.dmrc must be chmod 644. 
So I did all the necessary alterations and the problem is fixed.

---

