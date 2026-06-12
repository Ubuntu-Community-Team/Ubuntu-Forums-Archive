---
title: "gnome-session-flashback stops sticky-keys working"
date: 2018-09-01
forum: Desktop Environments
---

### Post by davaweb on 2018-09-01
Hi,
18.04.1

I did a clean install and sticky-worked OK.

I installed gnome-session-flashback and rebooted into ubuntu - sticky-keys still worked.

then I rebooted into metacity flashback and sticky-keys did not work. Checked it was still set (it was).

Can anybody suggest any help, please?

---

### Post by muktupavels on 2018-09-02
Unfortunately, this is regression! Please open upstream bug here:
[https://gitlab.gnome.org/GNOME/gnome-flashback/issues](https://gitlab.gnome.org/GNOME/gnome-flashback/issues)

In bug description please mention these links:
[https://bugzilla.gnome.org/show_bug.cgi?id=788564](https://bugzilla.gnome.org/show_bug.cgi?id=788564)
[https://gitlab.gnome.org/GNOME/gnome-settings-daemon/commit/9553071d0c26c3150a5f55bd93ebb4](https://gitlab.gnome.org/GNOME/gnome-settings-daemon/commit/9553071d0c26c3150a5f55bd93ebb4)

---

