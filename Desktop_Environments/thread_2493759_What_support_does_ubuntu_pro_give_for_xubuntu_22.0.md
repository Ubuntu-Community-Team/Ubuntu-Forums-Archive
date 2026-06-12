---
title: "What support does ubuntu pro give for xubuntu 22.04?"
date: 2023-12-23
forum: Desktop Environments
---

### Post by xode0000 on 2023-12-23
In particular, does ubuntu pro extend support for snap firefox and snap chromium?

---

### Post by ian-weisser on 2023-12-24
No, for two reasons:

1. Ubuntu Pro is for Ubuntu LTS releases only. That means Ubuntu Desktop (=Gnome) and Ubuntu Server only. Not other flavors. You can add Ubuntu Pro to your Xubuntu system, but Xubuntu 22.04 support will still end in April 2025 (3 years). Pro does not extend that for Xubuntu-specific packages. Pro does not provide security updates for Xubuntu-specific packages.

2. Snaps are supported by the snap author, not by Canonical or the Xubuntu Team. So the support-end-dates are largely irrelevant for Snaps. Snapd on all releases of Xubuntu (even releases past end-of-support) will continue to update Snaps when a new version is available from the author. Authors can discontinue snap support whenever they wish -- they are not bound by the Xubuntu Team's LTS promise of three years. Pro does not provide any additional snap-relates features or services or support.

Using any LTS flavor of *buntu past the 3-year life is a Very Bad Idea. Pro won't help enough. Don't do it.

---

