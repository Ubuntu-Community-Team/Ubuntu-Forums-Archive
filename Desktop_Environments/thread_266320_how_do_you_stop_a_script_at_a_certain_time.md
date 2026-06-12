---
title: "how do you stop a script at a certain time?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by jimisdead on 2006-09-27
At the moment I have a server with a tv card, and i record programs with 'dvbstream'. I can use 'at' to start recording a tv show at a certain time, but I don't know how to stop the program at a certain time (ie, when the program I am recording finishes) since the only way I know how to stop dvbsteram in Ctrl-c. Can anyone help? thanks.

---

### Post by gmc on 2006-09-27
Hi,

You could run **kill -9 `pidof <yourscriptname>`**, to kill the script say via a crontab entry. It's kludgy but should work.

G.

---

### Post by jimisdead on 2006-09-27
i'll try running that in another 'at' command... thanks. I hope it works. :)

---

### Post by gmc on 2006-09-27
> **jimisdead said:**
> i'll try running that in another 'at' command... thanks. I hope it works. :)

No Problem.

G.

---

