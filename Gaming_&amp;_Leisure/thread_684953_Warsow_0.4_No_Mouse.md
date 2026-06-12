---
title: "Warsow 0.4 No Mouse"
date: 2008-02-01
forum: Gaming &amp; Leisure
---

### Post by Biznarie on 2008-02-01
I installed warsow 0.4 on ubuntu, when i start the game my cursor will not move. I used the keyboard to get in a game and my mouse still wouldnt work, any suggestions?

---

### Post by shock2d on 2008-02-02
I found such solution:
after starting game go to the video settings using keyboard
press apply and mouse will work ok

But you need repeat it everytime you start the game

---

### Post by Biznarie on 2008-02-02
NIce, that works thanks man.

---

### Post by pizpot on 2008-03-11
OMG, I read this thread, didn't do anything, went back to warsow and it had fixed itself. :-) Oh, come to think of it, I did reboot, that would be it.

---

### Post by karth on 2008-03-12
It happens to me when I launch Warsow with compiz running. Disabling compiz before launching the game fixes everything.

---

### Post by Noccy on 2009-09-07
None of the suggestions in this thread works for me. On my laptop (Asus Aspire One, Ubuntu 9.04, Compiz enabled) everything works fine. On my desktop (P4 1.6GHz, Ubuntu 9.04) I can't move the cursor no matter what I select in the options, whether Compiz is enabled or not, nor if I launch it on the primary display or spawn a dedicated alternate display. Really annoying :/

Any ideas?

---

### Post by Perfect Storm on 2009-09-07
Try this;

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install compizconfig-settings-manager
ccsm
```

Click **General** category thereafter choose **General Options**.
In **General** tab, you'll see an option called; **Unredirect Fullscreen Windows**. Unselect it.


It might work.

---

