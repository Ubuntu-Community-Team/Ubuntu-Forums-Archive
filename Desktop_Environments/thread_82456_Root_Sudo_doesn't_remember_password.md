---
title: "Root Sudo doesn't remember password"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Leigh on 2005-10-26
According to the Wiki post regarding [RootSudo]("https://wiki.ubuntu.com/RootSudo") the password is supposed to be remembered for 15 mins. If memory serves me correctly, I seem to remember than in Hoary, when I used "Terminal" typing in "***sudo** whatever-command-I-want*", it would prompt me for the password the first time, but not again for that Terminal session. If I closed the terminal window and restarted , it would prompt me again the first time.  Breezy seems to prompt me everytime I type in a *sudo* command. Has something changed and can I get that functionality back?

---

### Post by Corvillus on 2005-10-26
sudo uses a timestamp to determine when was the last time you logged in. By default, the timestamp is 15 minutes if the timestamp_timeout option is not set in /etc/sudoers. You can edit this by typing sudo visudo and changing the number after the timestamp_timeout to the number of minutes you want the session to stay active.

---

