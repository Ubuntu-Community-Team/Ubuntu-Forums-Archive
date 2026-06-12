---
title: "Revert KDE to Original Settings [Resolved]"
date: 2007-01-30
forum: Desktop Environments
---

### Post by VoodooSteve on 2007-01-30
After many unsuccessful tries with KDE, I reinstalled Kubuntu from scratch. Now, since my home directory is on a separate partition, it made this process a lot easier. However, this also saved all my preferences. I don't want them anymore and would like to start from  scrath with KDE. If I were to delete the .kde directory in my home folder, would KDE recreate it with all the defaults? Or would this just cause more problems. Any suggestions?

---

### Post by ComplexNumber on 2007-01-30
> **VoodooSteve said:**
> After many unsuccessful tries with KDE, I reinstalled Kubuntu from scratch. Now, since my home directory is on a separate partition, it made this process a lot easier. However, this also saved all my preferences. I don't want them anymore and would like to start from  scrath with KDE. If I were to delete the .kde directory in my home folder, would KDE recreate it with all the defaults? Or would this just cause more problems. Any suggestions?
2 options:
-create a new user account
-at the login screen, choose failsafe terminal and delete the .kde directory.  then go back to the login screen and choose kde as your session. the .kde directory is the main 'settings centre', so that should do the trick. i would suggest that you delete everything in your home directory, but i can't confirm if such files as .bashrc etc wil be  recreated when you next login.

---

### Post by aysiu on 2007-01-30
Yes, KDE will recreate that directory if it's deleted.

I would suggest this command: ```
mv ~/.kde ~/.kde.old
``` That way, you'll still have your old settings if you want them back later, but they won't be used right now.

---

### Post by ComplexNumber on 2007-01-31
>  [quote]mv ~/.kde ~/.kde.oldThat way, you'll still have your old settings if you want them back later, but they won't be used right now[/quote]on second thoughts, thats an improved option on what i suggested. so, yes, i would recommend that too.

---

### Post by VoodooSteve on 2007-01-31
Thank you both. Worked perfectly. =D

---

