---
title: "Closing down GUI makes box unresponsive"
date: 2011-05-20
forum: Desktop Environments
---

### Post by lostterminal on 2011-05-20
Forum newbie here. Long-time Unix/Linux user, just got a new Xubuntu box set up to be a fileserver using SAMBA. I've noticed that every 8 minutes or so, the fileserver will disconnect any user currently accessing any files. My first instinct is to unload the GUI and tackle it from the terminal command line. However, every time I try to close out Xubuntu using "sudo init 1" I get taken to the Xubuntu splash screen and the box will no longer respond to any commands. Any help on either issue would be greatly appreciated. I can post any relevant information requested about the system, build, and version. Thanks in advance.

---

### Post by gsmanners on 2011-05-20
Xubuntu uses gdm, so you'll want to switch to tty (Ctrl-Alt-F1) and do:

```
sudo service gdm stop
```

That probably won't fix whatever Samba is doing, though.

---

