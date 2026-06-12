---
title: "Wine mIRC Crash"
date: 2009-05-29
forum: General Help
---

### Post by Greggaz on 2009-05-29
went to load mIRC Today in wine. it runs Great then i decided i would add scripts to my mIRC Opened Script editor it froze and Closed the full program any fixes or ideas?

---

### Post by madverb on 2009-05-29
Just use Xchat

---

### Post by Greggaz on 2009-05-29
im Wanting to use mIRC For my IRC Bot.

---

### Post by madverb on 2009-05-29
apt-get install eggdrop

---

### Post by Greggaz on 2009-05-29
i was told by a friend to click Disable Line Count or something but I cant even get to The Options for The script editor as when i open the script editor it waits about 3 seconds then crashes

---

### Post by madverb on 2009-05-29
you could try running it in a wine virtual desktop

---

### Post by Greggaz on 2009-05-29
i would Like to just run it in my machine not a virtual machine. I Think there may be an issue with Wine

---

### Post by madverb on 2009-05-29
It's not actually a virtual machine. It's an option in the Wine settings. Have a look through. Just see if it works while running in a **WINE** virtual desktop.

---

### Post by Greggaz on 2009-05-29
ok ill try that thanks for your help. you have been awsome

---

### Post by XCan on 2009-05-29
> **Greggaz said:**
> went to load mIRC Today in wine. it runs Great then i decided i would add scripts to my mIRC Opened Script editor it froze and Closed the full program any fixes or ideas?

There is a known bug in mIRC's script editor with Wine. Briefly, the line numbers won't show and full lines are cut at the beginning. This can be fixed either by turning off the line numbering in newer versions of mIRC or installing riched20 using winetricks.

Secondly, another annoying bug is /splay. If you call on it twice within a short time interval, mIRC will hang. For more information, check this page:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12568](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12568) .

---

### Post by Greggaz on 2009-05-29
ive installed ritched20 But the Script editor still crashes Anyone know what i can do?

---

### Post by XCan on 2009-05-29
Well what version of wine are you using? I'm running Wine 1.1.21, mirc 6.31 more or less 24/7 and haven't experienced any crash with or without script editor. :S

---

