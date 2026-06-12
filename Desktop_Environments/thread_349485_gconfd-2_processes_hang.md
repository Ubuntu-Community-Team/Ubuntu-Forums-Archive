---
title: "gconfd-2 processes hang"
date: 2007-01-30
forum: Desktop Environments
---

### Post by bpreindl on 2007-01-30
Hi,

I'm running an up-to-date 6.06 LTS server with gconf2 version 2.14.0. My problem is that some gconfd-2 processes seem to stay unterminated. If a user who's gconfd-process hasn't terminated after his last session, the user isn't able to login any more.

The only workaround is to kill -KILL every hanging gconfd-2 process manually for every user - a very annoying situation. By the way: Just kill doesn't work, it HAS to be kill -KILL.

An excerpt from the process list:

594      11460  0.0  0.3   6420  3856 ?        S    Jan16   0:00 /usr/lib/libgconf2-4/gconfd-2 5
731       9396  0.0  0.3   6428  3860 ?        S    Jan18   0:00 /usr/lib/libgconf2-4/gconfd-2 5
625      13679  0.0  0.3   6436  3872 ?        S    Jan18   0:00 /usr/lib/libgconf2-4/gconfd-2 5
641      20093  0.0  0.3   6436  3872 ?        S    14:58   0:00 /usr/lib/libgconf2-4/gconfd-2 5
650      15568  0.0  0.3   6424  3860 ?        S    15:59   0:00 /usr/lib/libgconf2-4/gconfd-2 5
730      16598  0.0  0.3   6444  3880 ?        S    16:00   0:00 /usr/lib/libgconf2-4/gconfd-2 11

The first three processes cause the user to be unable to login without maintainance. Her ./.xsession-errors is:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/ws206.ltsp:0.Xservers" -h "ws206.ltsp" -l "ws206.ltsp:0" "testuser"
/etc/gdm/Xsession: Beginning session setup...

I'd very happy if anybody knows what's going on here.

Thank you very much!

Bastian

---

### Post by engineer on 2007-01-30
did you try to delete or rename the ~/.gconf directory?

sometimes this is doing wonders!

---

### Post by bpreindl on 2007-01-30
Hi,

I didn't try to delete that directory but would it be have to be done everytime a user logs out or only once? I've about 120 users, so that wouldn't be very fine ...

Thank you very much!

Bastian

---

### Post by engineer on 2007-01-31
i thought it might help, if the data in .gconf are somewhat borked and the gconfd processes are hanging because of this.

if the problem is the same for all 120 users, there might be another reason.

---

