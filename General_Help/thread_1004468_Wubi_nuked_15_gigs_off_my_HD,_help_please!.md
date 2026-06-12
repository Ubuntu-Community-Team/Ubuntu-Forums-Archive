---
title: "Wubi nuked 15 gigs off my HD, help please!"
date: 2008-12-07
forum: General Help
---

### Post by altiod on 2008-12-07
[I posted this in "other" before, so reposting in the right location]

Hi everyone,

I recently tried to install wubi (kubuntu) on my lenovo x61. During installation (I believe it was while it was formatting the loopback partition exactly), the machine froze and forced me to reboot. It was stuck on a progress bar that was stuck at 66% and said it would be done in less than a minute. After about 20 minutes and a nonresponsive mouse it seemed pretty obvious it wasn't going to recover.

Scary enough, but I was able to boot back into windows no problem (cool), so I went to control panel and removed the installation in Add/Remove programs.

I rebooted the computer again and windows wanted to run checkdisk, so I let it do that - everything came through fine. Great. I finally get back into Windows, and everything seems to be working normally, aside from the fact that the 15 gigs I allocated to the installation are now gone. It seems like that should have been fixed when I uninstalled Wubi?

Anyway, is that 15 gig file sitting somewhere on my machine? Can I just delete it safely? I don't want to do anything to make this machine inoperable.

I don't think it makes a difference but I'm running windows server 2008.

Thanks a bunch! Also, if any of you know why it froze like that I would like to know. I'd be willing to try wubi again (maybe on a different machine) if i knew why the install went bad.

---

### Post by Yownanymous on 2008-12-07
Should be on the drive you installed wubi on, under the folder ubuntu. It is quite safe to delete that entire folder as long as you have uninstalled wubi.

---

