---
title: "Googsystray Icon disappeared"
date: 2011-09-08
forum: Desktop Environments
---

### Post by palimmo on 2011-09-08
Hello!

Happy Ubuntu 11.04 (Unity) user for several months.

From one day to another (perhaps in the meantime I did some general updates) Googsystray icon, which appears in the notification area (at least... I used to call it like this:)) when I receive e-mails, does not seem to work anymore.

- The Gmail account password is always the same one.
- The application is properly present in the 'Startup Applications ", in fact I can see the process in the system monitor (Status: Sleeping?).
- Alt-F2 -> D conf-editor -> Desktop -> unity -> panel
in systray-whitelist the value is always ['all'] (in fact the Skype icon, for example, appears normally).

What's happening?

Many thanks!

---

### Post by Frogs Hair on 2011-09-08
You could try to start the application from the terminal by entering the application name . Sometimes there will be messages if there is a problem of some kind .

---

### Post by shmibs on 2011-09-08
recently, google stated on their gmail sign in page that that page was going to be changing somehow soon. now, going to the sign in page, it appears that the domain name is accounts.google.com rather than mail.google.com. i'm having issues with my gmail checker as well, not being able to sign in, and i'm fairly certain this is it.

EDIT: saved passwords have the same issue, so your browser's saved usernames and passwords for gmail will have to be re-entered.

---

### Post by palimmo on 2011-09-09
> **shmibs said:**
> recently, google stated on their gmail sign in page that that page was going to be changing somehow soon. now, going to the sign in page, it appears that the domain name is accounts.google.com rather than mail.google.com. i'm having issues with my gmail checker as well, not being able to sign in, and i'm fairly certain this is it.

EDIT: saved passwords have the same issue, so your browser's saved usernames and passwords for gmail will have to be re-entered.

That could be!

Mmmhh.. and do you know if we can edit that address in Googsystray?

---

### Post by palimmo on 2011-09-09
I'm trying also here [https://sourceforge.net/projects/googsystray/forums/forum/1005366/topic/4699864](https://sourceforge.net/projects/googsystray/forums/forum/1005366/topic/4699864)

---

### Post by palimmo on 2011-09-10
Miracle!
Now it works!
:)

---

### Post by palimmo on 2011-09-11
> **palimmo said:**
> Miracle!
Now it works!
:)

Nooooooo!
It worked just for one day and now.. nothing! :(

---

### Post by palimmo on 2011-10-23
now I use gm-notify

---

