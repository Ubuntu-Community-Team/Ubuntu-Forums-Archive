---
title: "Stop timidity launching automatically?"
date: 2006-03-26
forum: Desktop Environments
---

### Post by [censored] on 2006-03-26
Hi. I installed timidity, the midi player, purely for its ability to convert midi to wav. Now it launches as a daemon automatically on boot up. I don't want to have to go through the trouble of killing it every time I log in, so how can I stop it doing that?

---

### Post by Sutekh on 2006-03-26
You should be able to disable the daemon from starting from the **Startup Programs** tab in System -> Preferences -> Sessions

---

### Post by [censored] on 2006-03-27
Dun work Sutekh. Thanks anyway. Tell you what does though .....

I found the timidity launcher script in /etc/init.d/, as well as a whole bunch of other launcher scripts. Working on the theory that all scripts in this dir get executed at bootup, I moved the script. I re booted, and my theory proved to be correct! No more timidity daemon running in the background.

---

