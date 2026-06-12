---
title: "pam, winbind and sudo problem"
date: 2005-12-06
forum: Desktop Environments
---

### Post by mcanada on 2005-12-06
I have a fresh install of Ubuntu 5.10 configured to authenticate with winbind and pam. I was initially impressed that the first attempt at this worked after reading the following article [http://ubuntuforums.org/showthread.php?t=5409]("http://ubuntuforums.org/showthread.php?t=5409").

I can successfully log into my PDC (Slackware 10.1 running Samba 3.020), no problem there. The problem that I have is that whenever the domain user tries to do a SUDO, it fails and pam winbind authentication no longer works after until I restart winbind.

I have ensured that the domain user is listed in the SUDOERS file but that has not fixed my problem.

Any suggestions would be greatly appreciated. I will post some of my configuration and logs.

---

### Post by mcanada on 2005-12-06
> /etc/pam.d/sudo
auth	sufficient	pam_winbind.so
auth	required	pam_unix.so nullok_secure use_first_pass


> /etc/sudoers
root	ALL=(ALL) ALL
mcanada     ALL=(ALL) ALL
%admin	ALL=(ALL) ALL


After attempting to do a SUDO with the domain user account:
> /var/log/auth.log
Dec  6 19:25:13 localhost pam_winbind[8556]: request failed: Invalid handle, PAM error was 4, NT error was NT_STATUS_INVALID_HANDLE
Dec  6 19:25:14 localhost pam_winbind[8556]: internal module error (retval = 4, user = `mcanada')
Dec  6 19:25:16 localhost sudo:  mcanada : pam_authenticate: Authentication service cannot retrieve authentication info. ; TTY=pts/0 ; PWD=/etc/pam.d ; USER=root ; COMMAND=/usr/bin/vi sudo


---

