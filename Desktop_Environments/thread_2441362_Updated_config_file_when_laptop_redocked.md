---
title: "Updated config file when laptop redocked"
date: 2020-04-22
forum: Desktop Environments
---

### Post by cAlpha on 2020-04-22
I have a Lenovo laptop on which I use Ubuntu 18.04 as my primary OS.  I use a laptop dock with this machine to which I have dual monitors connected.  

This works seemlessly, as I undock a few times per week, but has left me with a couple small issues:
(1)  I use conky and its alignment changes when I redock after being undocked (normally tr-aligned; redocking, it's aligned somewhere near the middle of the dual display).   

(2)  I have a MySQL installation which I commonly keep running for access throughout the day.  On one occasion, undocking before stopping MySQL caused a serious issue that prevented me from accessing it via any means, and I was only able to restore with a bit of luck.  As a result, I've been trying to stop MySQL before undocking, but do on occasion forget and undock without doing so.  **Wonder if there's a programmatic way to protect against this aside from being perfectly diligent.  **

For the first, I've historically simply killed conky via its pid and then restarted in the background via command line.  This works but is obviously manual.  Saving the conky.conf file, even if not updated, achieves a similar effect without needing to 'restart'.  **Is there any way to replicate this automatically upon redocking (ie, recognize machine is newly docked, run a command to realign conky display)?**

For the second, I can't conceptualize a good fix as stopping MySQL normally takes a few seconds and there isn't that much time between when I start to undock and the machine is disconnected.  Would welcome other thoughts about achieving this objective.

---

### Post by TheFu on 2020-04-23
Put a yellow sticky over the undock button as a reminder to run a script that does what you want?

It isn't like undocking is a computer controlled thing. It is a physical thing.

Hardware changes can usually be seen in the log files or through udev rules.  Perhaps you could look for those changes using a timestamp comparison with "now" compared to the log entries?

I don't use Conky or MySQL and wouldn't have a MySQL with anything important on a laptop.  I'd have mariaDB running on a desktop/server that doesn't move.

---

