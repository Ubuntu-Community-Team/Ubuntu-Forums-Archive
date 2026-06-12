---
title: "Login refused"
date: 2006-08-29
forum: Desktop Environments
---

### Post by beamish on 2006-08-29
Hi All,
I am unable to log-in to my machine after I had to press the interrupt button, except in maintenance mode.
When I boot to multi-user, entering any username at the console (non-graphical) just returns the prompt (kdm login fails as well). Attempting to ssh from another box returns a connection refused result.
I have checked all the disks, and they are fine, and not full.
/etc/passwd and /etc/shadow look fine. I cannot find anything in the logs to suggest why logins are refused.
Help!!!

---

### Post by funchords on 2006-08-29
Does the file /etc/nologin exist?

If so, delete it.

---

### Post by beamish on 2006-08-29
/etc/nologin doesn't exist. I am currently looking for corrupted files; is there any way to test the login process from a single-user shell?

---

### Post by funchords on 2006-08-29
Yes, give the command

**login**

You will be prompted for username and password for the new session.

Use **exit** or **logout** to return to your current session (depends on your shell).

---

### Post by beamish on 2006-08-29
Yes, thanks for that. I was getting a segfault when I tried it on my broken box, and assumed that it had to be run differently, hence my last question. I see now that after running it on my other box, it works as expected, so something is broken with login.
strace doesn't shed much light - it falls over just after closing /lib/security/pam_limits.so.
I have reinstalled login and util-linux without any change.

---

### Post by beamish on 2006-08-30
Well, the strace did give me a clue after all. I used the repository to find which package pam_limits lived in, (libpam_modules), and reinstalled that. Login now works as expected, and my machine appears to be back to normal. I will try my utmost to avoid pressing that reset button in future!
Thanks for your concern, and help.

---

