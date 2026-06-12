---
title: "Desktop shortcut to shell script"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by sanicki on 2007-06-07
Kubuntu 7.04

Using sshfs to mount external folders. Works fine from the command line. When I put it in a script and run the script from the command line it works fine. However when I create a desktop shortcut it runs and appears to work (asks for ssh pw, which indicates to me it's talking) but on exit folders aren't mounted.

Pls help.

---

### Post by bashologist on 2007-06-07
Did you try selecting "Application in Terminal" when you created the launcher? That might help.

---

### Post by sanicki on 2007-06-08
Yes. I'm baffled. The connection appears to be made (otherwise it wouldn't prompt for server-side pw, right?) but once it has finished running the mount hasn't been made. The script works like a charm from the command line.

---

