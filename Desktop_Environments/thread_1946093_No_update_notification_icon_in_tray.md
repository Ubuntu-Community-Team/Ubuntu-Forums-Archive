---
title: "No update notification icon in tray"
date: 2012-03-24
forum: Desktop Environments
---

### Post by Erik1984 on 2012-03-24
I run Kubuntu 11.10 and I noticed that when there are new updates I don't see any notification icon in the tray. When I was on Kubuntu Natty there was an icon with a cog and a green arrow in the tray whenever updates were available. It is not a big deal as I can manually check for updates in the Muon package manager now and then (and of course through the terminal) but I rather have some indication that updates are ready.

Maybe it has something to do with Muon Software Center not working? Muon Package manager works fine but the Muon Software Center crashes. This seems to be a known bug in Kubuntu as the crash report yielded tons of threads on bugs.kde.

---

### Post by schnelle on 2012-03-24
Update to latest stable muon.

```
sudo apt-add-repository ppa:echidnaman/qapt
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Erik1984 on 2012-03-24
Should I remove the version of muon software center I have now before installing this PPA?

---

### Post by schnelle on 2012-03-24
Just run above mentioned commands and optionally reboot system.

I am using newest muon. No crashes here and update notification icon appears in system tray :)

---

### Post by Erik1984 on 2012-03-25
Thanks you schnelle. The software center is working now.

---

### Post by Erik1984 on 2012-03-28
I'm marking this as unsolved :( Although the muon software center works now I still don't get the update notification icon in the tray. When I opened Muon Package Manager manually I saw 11 updates were waiting. The system does a daily updates check so when it finds updates then I expect some notification.

---

