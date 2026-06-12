---
title: "Is there a command to refresh pcmanfm simulating F5?"
date: 2012-07-24
forum: Desktop Environments
---

### Post by tanoloco on 2012-07-24
Hello,

I created a bash script which is run at startup which mounts some folders. The reason why I don't use fstab to do it is that a lot of users can access the system, so I created a common script rather than listing all the mounting points for each user in fstab.

Everything is working great, excecpt for the Desktop folder.
The mounted folder contains staff, but it's not shown on the user Desktop (wxin) nor listed in a pcmanfm window until I press F5 on a pcmanfm window at /home/user/Desktop

I mean: I have to open a pcmanfm window, goto /home/loggedUser/Desktop (which is shown as blank) and hit F5.
After that the pcmanfm window shows correctly the mounted content, which is also visible on the Desktop of xwin.

I tried
```
xrefresh
```
and
```
pcmanfm --desktop
```
without luck.

Any other idea?

---

### Post by tanoloco on 2012-07-24
I solved ending the script killing the pcmanfm process to restarting it again afterwards with
```
pcmanfm --desktop --profile lubuntu &
```

It works nice!
Thank you

---

