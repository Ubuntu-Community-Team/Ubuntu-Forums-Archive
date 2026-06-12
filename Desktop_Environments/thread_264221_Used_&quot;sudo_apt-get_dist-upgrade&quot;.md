---
title: "Used &quot;sudo apt-get dist-upgrade&quot;"
date: 2006-09-24
forum: Desktop Environments
---

### Post by joshier on 2006-09-24
Hello

I used this command and now my ubuntu will not logon.

It will boot up fine, and will automatically logon, but there appears to be an error upon logging on (perhaps one of the processes it launches automatically like Gaim) and it logs right back out.

I am unable to log in as root from the GUI shell, so I am not sure what to do.

Is there a roll back feature of some sort?

Thank you so much, I really miss my Ubuntu.. I want it back :(

---

### Post by ayoli on 2006-09-24
you may log as user in the shell, then if you need to grant root rights, use sudo.
once logged in the terminal, check .xsession-errors in your home dir (/home/user_name/.xsession-errors) you may find something, if it's an X problem check Xorg logs in /var/log/

---

### Post by joshier on 2006-09-24
> **ayoli said:**
> you may log as user in the shell, then if you need to grant root rights, use sudo.
once logged in the terminal, check .xsession-errors in your home dir (/home/user_name/.xsession-errors) you may find something, if it's an X problem check Xorg logs in /var/log/

OK thanks for your help.

Sadly my instillation CD has been scratched, so I'm downloading it again.

I am doing this because I am not too good with the command line, and prefer to use the live CD to mount the drive.

After I do this I'll post the logs up on here.

---

