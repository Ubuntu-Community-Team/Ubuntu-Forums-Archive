---
title: "Permission confusion"
date: 2006-09-16
forum: Desktop Environments
---

### Post by medicdave on 2006-09-16
OK, I'm having a n00b moment here...

I'd like to create a directory [/opt/usersfiles or something similar] then grant full permissions to all members of the users (GID=100) group on that directory. After using the GUI Users & Groups tool to make myself a member of 'users', I tried:

> cd /opt
> sudo mkdir testdir
> sudo chown root.users testdir
> sudo chmod 770 testdir
> cd testidr

And at that point, I get permission denied. This works fine on my Gentoo server, but for some reason Ubuntu doesn't seem to respect the middle octet of the permissions bits.

Can anyone give me some insight here?

Thanks,
[medic]Dave

---

### Post by nereid on 2006-09-16
The dot in the chown command should be a colon. Maybe your chown was not correct.

---

### Post by medicdave on 2006-09-16
Seems to behave the same either way...

---

### Post by nereid on 2006-09-16
Are you in the users group? As far as I remember Ubuntu is like BSD and creates for each user an own group.

---

