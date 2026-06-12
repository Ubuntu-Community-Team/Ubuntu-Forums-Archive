---
title: "password not asked on login, BUT, asked on screen lock?"
date: 2014-06-24
forum: Desktop Environments
---

### Post by Kilarin on 2014-06-24
I've got a computer with whole disk encryption and a single user.  Since you have to type in the drive password in order to boot the operating system, the user password seemed kind of redundant, so edited my user and set password to "Not asked on Login"  Which worked fine.

But then I noticed something I didn't like.  When my screen locks because I've been away from the computer for a while, it doesn't require a password to unlock it anymore.  Apparently unlocking the screen uses the same "Not asked on Login" setting.

I suppose there are folks who don't want their computer password protected at all.  But is there any way to set up a system so that the user password is not required on actual login, but still IS required when the screen locks?

---

### Post by 3rdalbum on 2014-06-25
Go to the Cog menu at the top-right corner of the screen, and select System Settings...

Click on Brightness & Lock, and turn the Lock switch on.

---

### Post by Kilarin on 2014-06-25
> **3rdalbum said:**
> Go to the Cog menu at the top-right corner of the screen, and select System Settings... Click on Brightness & Lock, and turn the Lock switch on.
Thank you very much for the advice.  Alas, it did not work.  Even when the lock switch is on, if the user has "do not ask password at login" set, then they can just hit enter and bypass the password.

---

### Post by buzzingrobot on 2014-06-28
Xubuntu uses "Light-Locker".  Check its entry in settings. Perhaps the adjustment you want is in there.

I believe there is also an occasional issue with XFCE locking the screen at the 10 minute mark regardless of the user's configuration.

---

### Post by Kilarin on 2014-06-30
[quote="buzzingrobot"]Xubuntu uses "Light-Locker"[/quote]
Yep, that's where I turned the lock on and it still allowed me in by just hitting enter if the user is set to "do not authenticate on login"

[quote="buzzingrobot"]I believe there is also an occasional issue with XFCE locking the screen at the 10 minute mark regardless of the user's configuration. [/quote]
Except in my case, the problem is that it wont lock.  Ah well.  I can live with typing in passwords twice when logging in.

---

