---
title: "60 second boot-up pause under 8.10"
date: 2009-03-07
forum: General Help
---

### Post by Billsey on 2009-03-07
[This thread]("http://ubuntuforums.org/showthread.php?t=1058502&highlight=boot-up+pause") might discuss a related problem, but I don't think so. My problem is that when I boot up my HP Pavilion ze2000 (2GHz with 1.25GB RAM and a 160 GB hard drive), the progress bar gets about 2/5 to 1/2 through the bar, then pauses for 60 seconds (I timed it) before continuing with the boot (this is repeatable every time). Is there a simple way that I can safely eliminate, or at least greatly reduce, this pause?

If possible, [EMAIL="lt@billsey-christian.net"]EMail me[/EMAIL] with the answer.

---

### Post by Svensk023 on 2009-03-07
have you created a read-ahead profile ever?

---

### Post by Slim Odds on 2009-03-07
Boot without the "quiet" option and see what's happening while the long delay is going on.

Reboot and press <Escape> to get to the boot menu.
Select the default boot option and press "e" to edit
Remove "quiet" and press <Enter>
Then press "b" to boot.....

Watch and wait.....

---

