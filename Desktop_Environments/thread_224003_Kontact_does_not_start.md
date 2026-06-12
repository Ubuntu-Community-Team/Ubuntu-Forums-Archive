---
title: "Kontact does not start"
date: 2006-07-27
forum: Desktop Environments
---

### Post by poekie on 2006-07-27
Hi

Yesterday, Kontact worked fine, one crash after some weird hanging of an IMAPfolder, but it restarted normally after that. Today, nothing. It will not start. It does ask me for my KWallet password, but then it stops. KSysguard sees it, so there is something going on (with CPU at about 30-50), but no window appears. It also shows that the two IMAPfolders are trying to check for mail as there are two imapconnections in Ksysguard. I've tried gdb but that just stops logging or something after KWallet dialog appears, which is just before it 'crashes' if you can call it that, and thus nothing about the high CPU. 

This is Kubuntu 6.06, updated every week (today, after all these problems, as well) so no out-of-date packages I can think of.. I tried removing these folders as I read somewhere that those might be corrupted but to no avail, after reboot, still no Kontact.
.kde/socket-jet 
.kde/tmp-jet
.kde/cache-jet

Any help?

---

### Post by GuitarHero on 2006-07-27
Did you try starting the program through the terminal?  That would most likely give you the error thats causing the problem.

---

### Post by poekie on 2006-07-27
> **GuitarHero said:**
> Did you try starting the program through the terminal?  That would most likely give you the error thats causing the problem.

It does the same as gdb: it stops saying anything after the KWallet thingie comes up for my password. CPU skyrockets and nothing happens..

---

### Post by poekie on 2006-07-27
After finding out that Korgac was also skyrocketing CPU usage (Kontact and Korgac were using about 80% together) I googled some more and I found a workaround/solution: probably a calendar Korgac was trying to load was faulty.
I replaced my std.ics file with it's backup of yesterday morning, started Kontact and it actually started! :D

---

