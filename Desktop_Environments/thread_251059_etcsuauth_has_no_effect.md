---
title: "/etc/suauth has no effect"
date: 2006-09-04
forum: Desktop Environments
---

### Post by g4c9z on 2006-09-04
Hello,

I'm not sure if this is the right forum to ask this, but I'm having trouble with my /etc/suauth file.  According to its man page (which I found on the internet), su is supposed to read it and it allows users to su to other users without a password.  On my old Gentoo system, I was using it to allow myself to su to root without a password, and prevent anyone but me from becoming root, whether they know my password or not.  I want the same behaviour on Ubuntu, so I copied the file, which is as follows:

```

root:adam:NOPASS
root:ALL EXCEPT adam:DENY
```

But su still asks me for a password.  Why?

---

### Post by g4c9z on 2006-09-09
I figured out the problem.  Ubuntu installs PAM, for some reason, which overrides su's regular file.  So I had to edit /etc/pam.d/su to get this kind of thing to work.

---

### Post by electrofox on 2008-06-06
Thanks a bunch, g4c9z! This had me stumped for a little while.
-ElectroFox

[COLOR="White"]ubuntu
suauth
pam
pam.d
su
block su users groups
wheel[/COLOR]

---

