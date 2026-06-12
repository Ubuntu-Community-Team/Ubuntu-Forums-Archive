---
title: "[SOLVED] Soft Links"
date: 2008-12-20
forum: General Help
---

### Post by fuzzybear3965 on 2008-12-20
Okay so this is my problem.  I have a Linux mint desktop that I want to link to my Ubuntu desktop so that I can see all my desktop items on one screen.  I know it's a soft link command I need but I keep screwing up the syntax and my desktop has an icon which links to the directory and does not display the contents of the Linux mint desktop.

ln -s /media/mint/home/john/Desktop /home/john/Desktop is what I have been using.  but obviously that's not working.  Respond ASAP.  Thanx

---

### Post by dcstar on 2008-12-20
> **fuzzybear3965 said:**
> Okay so this is my problem.  I have a Linux mint desktop that I want to link to my Ubuntu desktop so that I can see all my desktop items on one screen.  I know it's a soft link command I need but I keep screwing up the syntax and my desktop has an icon which links to the directory and does not display the contents of the Linux mint desktop.

ln -s /media/mint/home/john/Desktop /home/john/Desktop is what I have been using.  but obviously that's not working.  Respond ASAP.  Thanx

You cannot link to an existing file (/home/john/Desktop), and you cannot delete/rename that because you are using it when you log in with that account.

---

### Post by logos34 on 2008-12-20
so the best thing is maybe relabel the mint partition with Dekstop as "Mint"--its icon will show up on your ubuntu desktop and in the nautilus side pane.

---

### Post by fuzzybear3965 on 2008-12-20
Thanks all. I fixed it with this:  ln -s /media/mint/john/Desktop/* /home/john/Desktop.   Works great, thankx

---

