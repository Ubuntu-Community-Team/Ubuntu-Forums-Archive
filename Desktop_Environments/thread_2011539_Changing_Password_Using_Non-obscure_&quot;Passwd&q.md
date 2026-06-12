---
title: "Changing Password Using Non-obscure &quot;Passwd&quot; Broke Screen-saver Unlocking"
date: 2012-06-27
forum: Desktop Environments
---

### Post by user2037 on 2012-06-27
Now that I've removed the "obscure" requirement from PAM and changed my password with "passwd" I can not unlock my screen saver.

Changing to Gnome-screensaver does not help. Changing back to my original password does not help. Attempts to change my password from the Users-and-groups UI does not change the password at all.

Any ideas?

EDIT: I've managed to change the password from Users-and-groups after some repeated attempts, but then had to change Keyring password to match. Still the screen-saver lock continues to deny the current and past passwords.

EDIT2: Here is the /var/log/auth.log:
Jun 28 13:37:05 myworkstation login[2337]: pam_unix(login:session): session opened for user myuser by LOGIN(uid=0)
Jun 28 13:37:20 myworkstation gnome-screensaver-dialog: pam_tally(gnome-screensaver:auth): Error opening /var/log/faillog for update
Jun 28 13:37:30 myworkstation gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): conversation failed
Jun 28 13:37:30 myworkstation gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): auth could not identify password for [myuser]
Jun 28 13:37:30 myworkstation gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): getting password (0x00000388)

EDIT3: Finally fixed when I realized "auth required pam_tally.so onerr=fail deny=5 unlock_time=21600" in /etc/pam.d/common-auth was not appropriate for my version of Ubuntu (and/or perhaps misplaced).

---

