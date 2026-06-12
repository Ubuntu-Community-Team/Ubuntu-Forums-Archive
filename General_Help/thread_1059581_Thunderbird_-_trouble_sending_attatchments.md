---
title: "Thunderbird - trouble sending attatchments"
date: 2009-02-03
forum: General Help
---

### Post by clickwir on 2009-02-03
Same problem as this guy. ::: [http://ubuntuforums.org/showthread.php?t=337181](http://ubuntuforums.org/showthread.php?t=337181)

Can send an email without an attachment just fine, but with an attachment it doesn't send, changing the MTU fixes.

Unfortunately, I'm using MTU 9000 for my gigabit network. If I change the MTU to 1500, the email with attachment sends fine. But I can't go changing my MTU every time I want to send an email with an attachment.

Kubuntu Intrepid 64
Thunderbird version 2.0.0.19 (20090105)

When using MTU 9000, everything else with the system seems to work fine, has been for quite some time. Just sending emails with attachments fails.

What can I do to fix this? Should I file a bug report? :-)

---

### Post by clickwir on 2009-07-10
Still have this issue. If I change the MTU to 1500, it works fine. But at 9000, it has issues. So far, Thunderbird is the only app with an issue.

---

