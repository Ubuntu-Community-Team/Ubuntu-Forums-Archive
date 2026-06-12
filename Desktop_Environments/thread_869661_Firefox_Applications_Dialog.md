---
title: "Firefox Applications Dialog"
date: 2008-07-25
forum: Desktop Environments
---

### Post by maxomai on 2008-07-25
Hey all.

So I'm using Firefox 3 on Kubuntu, and it's driving me nuts. Whenever I try to open a PDF or a directory, it opens a session of OpenOffice and tries to open that entity as a text document. The expected behavior, of course, is that it will open the directory in a file explorer like Dolphin and a PDF in kpdf or adobe.

I've tried going into the applications dialog, and the dialog shows no applications preferences whatsoever. And when I go into about:config, a search for oowriter (or even "oow") reveals nothing.

How do I fix this? It's to the point where I'm ready to do a clean re-install of the OS.

---

### Post by cpetercarter on 2008-07-25
There is a reported bug (see [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798")).
The workaround appears to be to install the firefox-gnome-support package
```
sudo apt-get install firefox-3.0-gnome-support
```

---

### Post by kirillkh on 2008-12-27
Thanks a lot! Did the trick for me.

---

