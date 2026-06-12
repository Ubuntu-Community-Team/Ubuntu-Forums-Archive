---
title: "kde4 version of kmail won't create sending account"
date: 2008-09-17
forum: Desktop Environments
---

### Post by mwolthers on 2008-09-17
I've got a serious problem here with kmail since I upgraded from Hardy/KDE3.5.10 to Intrepid/KDE4.1.1. The new kmail took over all of my old account information like it should except for my sending account. Maybe a little bug I thought, so I went on creating my sending account again. After entering my outgoing SMTP server and an account name I pressed OK and... my window disappeared and my would-be-created account was nowhere at all! I've tried purging and re-installing kmail but that actually left my accounts in tact (I suppose PIM takes care of my accounts) and didn't allow me to create the sending account. I tried installing mailody-kde4 and to my surprise it had the exact same error.

I'm getting really frustrated by having to open my (sloooowww) webmail everytime I need to send an e-mail. So if anyone can give me a clue as to what's happening here, that would be more than welcome!

---

### Post by Pro-reason on 2008-09-17
Report it: [http://bugs.kde.org](http://bugs.kde.org)

---

### Post by mwolthers on 2008-09-22
Does no-one recognize this problem? I don't know if it's a bug or a misconfiguration within my own system, that's why I didn't report a bug. Given the zero useful replies I don't really expect it to be a bug. So, anyone, please??

---

### Post by Pro-reason on 2008-09-22
The fact that no one has any suggestions doesn't mean that it is not a bug.  On the contrary, if it were a common misconfiguration, we could tell you how to fix it.  It looks very much like one of the many KDE 4 bugs that have driven me to use GNOME.

Ubuntu is GNOME-based, and Hardy is the latest release.  There are very few people using KDE 4 on Intrepid.  You can't expect there to be many people who can chime in, reporting the same problem.  There always has to be someone who reports the bug first.

Make more of an effort to find the configuration files that Kmail/Mailody use.  They must be somewhere in ~/.kde4/.  If that still doesn't work, report the bug to KDE.

---

### Post by pliscante on 2008-10-15
I encountered the same problem today.  Have you found a solution yet?

---

### Post by Pro-reason on 2008-10-15
I have (downloaded today) the latest version of KMail from Kubuntu Intrepid.  It works fine.  Perhaps you could try completely removing all the relevant software (including stuff like PIM that could be retaining personal data) and reinstall/upgrade.

If it still presents the bug, then report it.

---

