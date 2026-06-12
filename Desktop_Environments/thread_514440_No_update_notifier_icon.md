---
title: "No update notifier icon"
date: 2007-07-31
forum: Desktop Environments
---

### Post by AndyPopely on 2007-07-31
I don't automatically get the system updates notifier icon anymore when there are updates.  I don't know when this stopped happening.

When I suspect there are updates for my Feisty Fawn system I start the update manager ... system -> administration -> update manager.  On the update manager window I press the check button.   I then get asked for my password.  Then the repositories are checked and after several seconds the update manager shows the list of updates.

If I ignore the updates and close the update manager and then close and restart Feisty Fawn as soon as I connect to my router the system updates notifier icon appears in the notification area.

So the bootom line is I don't get notified automatically of system updates I have to manually check for them first.

Anyone any ideas please .....

---

### Post by pedrogl on 2007-08-02
Check: System -> Administration -> Sessions
There should be a (checked) entry called "Update Notifier", if not, add one with the command "update-notifier"

---

### Post by pedrogl on 2007-08-02
Sorry, I didn't read carefully. I don't think my previous post help to solve your problem :(
But, if undestood well, on my box there is a file /etc/cron.daily/apt which, I suspect but not sure, is responsible to assure every day your system check for updates.
If that is really the case, I don't know how to fix it, except by reinstaling apt/anacron (?).

---

### Post by rkh on 2007-08-03
Mine was gone for a few months. I fixed it literally moments ago! Try right-clicking on the panel then Add to Panel. Scroll down to Utilities. Click on Notification Area.

---

### Post by AndyPopely on 2007-08-03
Solved ... the problem was anacron wasn't being scheduled ... I installed and ran sysv-rc-conf and reinstated anacron being scheduled and all is well

---

