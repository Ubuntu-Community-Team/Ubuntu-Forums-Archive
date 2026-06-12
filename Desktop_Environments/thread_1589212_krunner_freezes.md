---
title: "krunner freezes"
date: 2010-10-06
forum: Desktop Environments
---

### Post by Stok on 2010-10-06
I just switched from Gentoo to Kubuntu after having used the former for 5 years. Before that I used Ubuntu and Debian. Anyway, whilst most of apps seem to work perfectly, krunner tends to freeze from time to time. I press alt-f2 (or run krunner from xterm), it pops up, but there's the command from last time, I'm unable to type new, delete or execute the last command, though other buttons work and esc closes the pop-up. I killed the process and re-run krunner from xterm and it works again, but I'm not satisfied with the situation. Has anybody experienced the same problem and somehow overcome it?

---

### Post by ankspo71 on 2010-10-06
Hi, 
Does the runner at the top of your Kmenu still work?

Krunner might have a bad configuration file. Try using this command in Konsole to see if it will help fix Krunner.
```
mv ~/.kde/share/config/krunnerrc ~/.kde/share/config/krunnerrc.backup
```
All that command does is renames the configuration file of Krunner to a backup file that can be restored later if needed. The next time Krunner needs a configuration file it will automatically be created.

Hope this helps.

---

