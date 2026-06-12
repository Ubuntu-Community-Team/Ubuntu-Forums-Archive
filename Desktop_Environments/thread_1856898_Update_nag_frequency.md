---
title: "Update nag frequency"
date: 2011-10-09
forum: Desktop Environments
---

### Post by treacl on 2011-10-09
With reference to [this old thread]("http://ubuntuforums.org/showthread.php?t=323093"), is there a built-in way to have it nag once a week instead of every single friggin time I turn my computer on?

If not, any suggestions re the most efficient way of doing this? Use anacron (I have some experience with cron, but none with anacron)? Point the session startup item to a shell script that checks when it last nagged and, if more than a week ago, runs the nag program? Any other ideas?

Thanks,
treacl

---

### Post by Krytarik on 2011-10-09
Already had a look at the options under "Software Sources -> Updates -> Automatic updates" (under "System -> Administration" in classic Gnome)!?

Regards.

---

### Post by treacl on 2011-10-09
In 10.04, at least, that seems to control how often it checks for new updates, not how often it nags you about them: I have long had it set to "weekly," but it still nags me at every startup.

---

### Post by Krytarik on 2011-10-09
> **treacl said:**
> In 10.04, at least, that seems to control how often it checks for new updates, not how often it nags you about them: I have long had it set to "weekly," but it still nags me at every startup.
Well, you do know that you need to allow the updates to make your so-called "nag" disappear, right!?

Otherwise, you would need to disable "Update Notifier" in "Startup Applications", as mentioned in the thread you referred to.

And yes, I, too, have set it to "weekly"; it "nags" me once a week, I apply the updates, and fine. ;-)

---

### Post by hansdown on 2011-10-09
> **Krytarik said:**
> Well, you do know that you need to allow the updates to make your so-called "nag" disappear, right!?

Otherwise, you would need to disable "Update Notifier" in "Startup Applications", as mentioned in the thread you referred to.

And yes, I, too, have set it to "weekly"; it "nags" me once a week, I apply the updates, and fine. ;-)

+1.

If you don't install the updates, the "nag" feature kicks in, until you install the updates.

Hope this helps,treacl.

---

### Post by Frogs Hair on 2011-10-10
I think installing updates is the best solution  ; however , I think the package update-notifier-common is what generates the message .

---

