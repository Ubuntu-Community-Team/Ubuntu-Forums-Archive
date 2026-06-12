---
title: "How can I add a logoff sound in the GNOME desktop?"
date: 2023-04-12
forum: Desktop Environments
---

### Post by chris0nlinux on 2023-04-12
Hello everyone,

I have just discovered that the Yaru sound theme has a login and logoff sound! I managed to enable the login sound by adding ```
mpv /usr/share/sounds/Yaru/stereo/desktop-login.oga
```in Startup Applications but I can't enable the logoff sound. Can somebody please help me enable the Yaru logoff sound?

Thank you,
Chris

---

### Post by TheFu on 2023-04-12
I don't know of any specific "shutdown" event that gets sent.  That means the only way would be to replace existing shutdown with your own version that plays a sound before doing the normal shutdown.

Hummmm.  You could create a new systemd Unit files that gets fired as part of the shutdown process.  Something to be the cournterpart to /etc/systemd/user/graphical-session-pre.target.wants/ unit files?

Or look for 1 job in the output from 
```
/bin/systemctl list-jobs shutdown.target
```
The script would need to run every 10 seconds or so. It is a polling solution. Not exactly efficient.  For efficiency, I'd try to hook into the graphical-session shutdown event that systemd should call for a properly setup unit file. [https://www.freedesktop.org/software/systemd/man/systemd.unit.html](https://www.freedesktop.org/software/systemd/man/systemd.unit.html) is the documentation.

---

### Post by chris0nlinux on 2023-04-12
I added my script in /usr/lib/systemd/system-shutdown and it works!

---

### Post by ActionParsnip on 2023-04-13
Please mark as solved if the issue is sorted :P

---

### Post by TheFu on 2023-04-13
> **chris0nlinux said:**
> I added my script in /usr/lib/systemd/system-shutdown and it works!

Be careful placing anything under /usr/lib/, since that isn't where custom stuff belongs.  You'll need to add that area/script top your backup list as well, regardless of where you place it.  Generally, it is best to find the correct location under /etc/ for stiff like this, since everything in /etc/ should be backed up, if only for reference during system recovery.

---

### Post by ActionParsnip on 2023-04-13
> **TheFu said:**
> Be careful placing anything under /usr/lib/, since that isn't where custom stuff belongs.  You'll need to add that area/script top your backup list as well, regardless of where you place it.  Generally, it is best to find the correct location under /etc/ for stiff like this, since everything in /etc/ should be backed up, if only for reference during system recovery.

+1

You can add an override file to update the files so then updates don't overwrite your efforts

---

