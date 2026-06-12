---
title: "Built-in file manager after purge thunar"
date: 2013-06-17
forum: Desktop Environments
---

### Post by darkpepe on 2013-06-17
Hi,

I'm using Xubuntu 12.04 and Xfce 4.10 (through PPA) I'm quiet happy with it, but for the terrible system lockups (not even REISUB works) when browsing through network shares with Thunar. Nautilus seems to be working fine though.

Unfortunately, I noticed that the "save-as" dialogues will not use nautilus with all programs (LibreOffice uses the exo file manager, Firefox does not e.g.).

After executing sudo apt-get purge thunar* nautilus*, there is no file manager installed on my system. Yet, I can browse directories inside the "open" and "save" dialogues of different programs.

What is being used to do so, and how do I replace it with whatever does not lock my system?

Thanks,

Joe

---

### Post by brainwash on 2013-06-17
The GtkFileChooser is being used for most open/save dialogs.

---

### Post by darkpepe on 2013-06-17
> **brainwash said:**
> The GtkFileChooser is being used for most open/save dialogs.

Thanks!

I'm googling about replacing it, but with very little success. I wouldn't want to move from GTK to QT....

Any ideas?

---

### Post by mcduck on 2013-06-17
There really isn't anything you could do about it, it's not a file manager or separate application but a widget provided by the GTK toolkit, so the only people able to replace it with something else or change the features used in some program are the developers themselves.

You should probably try to find out why the network shares are causing lockups and try fixing that instead...

---

### Post by darkpepe on 2013-06-18
> **mcduck said:**
> 
You should probably try to find out why the network shares are causing lockups and try fixing that instead...

You are right, but the crash is leaving no log. Can you point out how to trace this lockups?

Thank you,

Joe

---

### Post by TiberiusT on 2013-06-18
As a Xubuntu user for over 2 years I used to experience similar issues with Thunar and Network shares - I almost ditched the entire XFCE desktop bcos of it. But in the last 12 months newer versions of Thunar have addressed all the issues for me and the version with 13.04 has tabs as well. It runs faultlessly accessing my NFS and Samba shares - it's definitely fixed as far as I am concerned. 

T

---

