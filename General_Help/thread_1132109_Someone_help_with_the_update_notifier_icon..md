---
title: "Someone help with the update notifier icon."
date: 2009-04-21
forum: General Help
---

### Post by rajeev1204 on 2009-04-21
Hi

I tried the workaround for update notifier in gconf-editor but i still dont get that orange icon in panel except when manually launching it it shows in panel.

Here are my settings of gconf for update manager and notifier

---

### Post by rajeev1204 on 2009-04-27
bump.

---

### Post by rajeev1204 on 2009-04-28
I have tried the fix to get old notifier back but it only shows icon in tray when manually running update -manager.

Its been a few days and i havent got any updates.

ANyone got any updates in jaunty?

---

### Post by Brandon Williams on 2009-04-28
The fix works exactly as intended for me. Are you sure that you have updated your package sources? And after the updating the sources, are there any upgrades to be applied?

In a terminal, run 'sudo aptitude update' and then 'sudo aptitude -s full-upgrade'. The first command updates your sources and the second command will simulate an upgrade. If the second command tells you that there are upgrades to apply, then the update-notifier icon should appear in your status tray, since you appear to have update-notifier configured correctly. This is what happens for me.

---

### Post by rajeev1204 on 2009-04-30
> **Brandon Williams said:**
> The fix works exactly as intended for me. Are you sure that you have updated your package sources? And after the updating the sources, are there any upgrades to be applied?

In a terminal, run 'sudo aptitude update' and then 'sudo aptitude -s full-upgrade'. The first command updates your sources and the second command will simulate an upgrade. If the second command tells you that there are upgrades to apply, then the update-notifier icon should appear in your status tray, since you appear to have update-notifier configured correctly. This is what happens for me.

You dont understand the problem.Running those commands is equivalent to running update -manager manually.

It was done automatically everyday and the notifier glowed when updates were available.

---

### Post by Brandon Williams on 2009-04-30
I fully understand the problem. I was trying to give you a way to determine whether there are actually any updates for you to be notified of. You cannot know whether the setting has worked to changed the behavior unless you know that it _should_ be appearing in the system tray.

For me, the icon appears when updates are available. It appeared quite regularly between beta and release, less so now.

---

### Post by rajeev1204 on 2009-04-30
> **Brandon Williams said:**
> I fully understand the problem. I was trying to give you a way to determine whether there are actually any updates for you to be notified of. You cannot know whether the setting has worked to changed the behavior unless you know that it _should_ be appearing in the system tray.

For me, the icon appears when updates are available. It appeared quite regularly between beta and release, less so now.

Hi brandon. Thanks for replying.

But iam still not getting what you are saying.A few days ago,i.e.2 days before final release i ran those commands after which i got those orange icon.

Later i havent done anything.You mean maybe there are no updates yet?

---

### Post by Brandon Williams on 2009-04-30
I'm suggesting that either there are no updates for you or you don't have your system configured to update the software sources as often as you would like. Provided that the software sources are being updated _and_ there are updates then the icon should be appearing for you ... it does for me anyway.

If running apt-get update makes the icon appear, then I suspect that you aren't updating the software sources daily. Double-check the updates tab in 'Software Sources' and verify that both jaunty-security and jaunty-updates are being pulled, and that you are checking for updates daily.

If the icon doesn't appear after apt-get update but a simulated upgrade says that it will upgrade a bunch of packages, then you're experiencing a problem that I'm not experiencing.

---

### Post by rajeev1204 on 2009-05-03
> **Brandon Williams said:**
> I'm suggesting that either there are no updates for you or you don't have your system configured to update the software sources as often as you would like. Provided that the software sources are being updated _and_ there are updates then the icon should be appearing for you ... it does for me anyway.

If running apt-get update makes the icon appear, then I suspect that you aren't updating the software sources daily. Double-check the updates tab in 'Software Sources' and verify that both jaunty-security and jaunty-updates are being pulled, and that you are checking for updates daily.

If the icon doesn't appear after apt-get update but a simulated upgrade says that it will upgrade a bunch of packages, then you're experiencing a problem that I'm not experiencing.

Hi

I have checked all in synaptic.

Waiting for updates now. Have you received any new updates ?Do let me know.



regards
rajeev

---

