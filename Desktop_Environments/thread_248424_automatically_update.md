---
title: "automatically update"
date: 2006-09-01
forum: Desktop Environments
---

### Post by tofool on 2006-09-01
Hello everyone. I just received ubuntu cds in the mail and I am quite impressed by the quality put into the presentation (nice cd cases and stickers too!) Thanks Canonical!

Anyhow, I installed Ubuntu on my sister's computer and she has a sub-average IQ so I would like to enable automatic updates. In the Software Preferences > Internet Updates window I see 3 options.

None of them mention anything about automatically installing except the 3rd option -- install security updates without confirmation.
If possible I'd like to extend the 3rd to all updates.

I know I can write a perl or shell script but by any chance is there something better already made / built in?

PS. Ubuntu kicks ***!

---

### Post by Jussi Kukkonen on 2006-09-01
> None of them mention anything about automatically installing except the 3rd option -- install security updates without confirmation.
If possible I'd like to extend the 3rd to all updates.

Just think carefully about this -- every upgrade is a possible point of breakage (as was seen in the xserver issue some time ago). Would your sis want to increase the risk of something getting broken without any discernible improvement (assuming the apps she uses already work)? If it ain^t broke, don^t fix it...

*cron-apt* is probably what you're looking for, if you really want to do it.

---

### Post by FuriousLettuce on 2006-09-01
Software updates within Ubuntu, apart from security updates, are generally designed to add small amounts of features or fix small bugs. Major functionality changes only really come with each new release (5.10, 6.06 etc). I would recommend that you do as Jussi suggests and simply ignore any updates that aren't security.

---

