---
title: "Logging in to nothing.."
date: 2006-07-11
forum: Desktop Environments
---

### Post by R32 on 2006-07-11
I just accepted the upgrades that were offered this morning. I didn't really even look at them, except that there was a kernel upgrade and a new fglrx package, and the installer went on and installed the packages and requested a reboot. Fair enough. So, I rebooted and tried to log in and all I got was the mouse pointer. It never progresses to Gnome. So, I thought it must have been the XGL, I restarted GDM and tried the user without any XGL. Same thing. I then created a new user from the shell, and was able to log in with that one. Weird.

I thought it might have been the previous .gnome related files, so I removed everything from my normal login's home folder to a different place, but that didn't work. Since I now had a login from a new user, I tried adding admin priviliges to the account and once I had them set and logged out, the same thing happened, just a blank screen. 

I can create a normal user with no priviliges whatsoever and I can login with that. But as soon as I add any rights, the login fails. And none of my old logins work either.

Maybe it's session related? Does anyone have any ideas as to what could have gone wrong? Or where I can find the solution to this annoying problem?

I'm using Dapper Drake, with and without XGL, and all of the latest updates as of this morning.

Thanks in advance.

---

### Post by R32 on 2006-07-11
Ok, just figured out that it's the Audio device. If I add anyone to the Audio group, I can't login to gnome. It just hangs. Checked the modules, they all seem fine. Any ideas anyone?

---

### Post by R32 on 2006-07-11
Well, this doesn't seem to make sense. It can't be the kernel versions, as I booted with the new kernel and the last one, and the drum beat sound is played at the login screen both times.

How would I go about reinstalling the ubuntu sound drivers?

Thanks

---

### Post by R32 on 2006-07-13
fixed

---

