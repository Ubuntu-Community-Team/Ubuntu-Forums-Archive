---
title: "User missing from KDE login screen"
date: 2013-07-30
forum: Desktop Environments
---

### Post by drogo1127 on 2013-07-30
I changed my uid (from 1000 to 500) to access an NFSv4 filesystem and after booting back up, my user is no longer listed as a login option on the KDE screen. Only "guest" is shown. Do I have to do something to tell KDE about the users available in the system?

Console login works fine.


Thanks.

---

### Post by Cheesemill on 2013-07-30
By default only users with a UID of 1000+ are shown by the display manager as UID's less than 1000 are usually reserved for system accounts.

Try editing the /etc/kde4/kdm/kdmrc file and changing the MinShowUID variable.

---

### Post by drogo1127 on 2013-07-30
I checked, and didn't have that file, so I created it and put in MinShowUID=500, but it still only shows the guest user. (This is 13.04 kubuntu).

Running "find / -type f -iname "*kdmrc*" didn't return anything before creating it.

---

### Post by drogo1127 on 2013-07-30
I also tried MinShowUID=499, no luck there, either.

---

### Post by steeldriver on 2013-07-30
If you don't have /etc/kde4/kdm/kdmrc then likely you are not running kdm as your display manager - I think possibly kubuntu switched to lightdm as the default dm in 13.04?

If that's the case, then the equivalent file would be /etc/lightdm/users.conf and the parameter to change is minimum-uid

```

[UserAccounts]
[B]minimum-uid=500
[/B]hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

---

### Post by drogo1127 on 2013-07-30
That was it. 

I already had the above entries in users.conf, so I checked /etc/login.defs (saw the comment in users.conf about AccountsService) and changed the UID_MIN & GID_MIN settings down to 500 from 1000. Now my acct shows on the KDE login screen.

Thanks!!

---

