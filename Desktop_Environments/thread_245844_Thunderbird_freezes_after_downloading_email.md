---
title: "Thunderbird freezes after downloading email"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Ndlovu on 2006-08-28
I've been the victim of a rather annoying bug the last couple of days. Thunderbird (1.5.0.5 on dapper) is freezing as soon as it's downloaded email. I have not made any (deliberate) changes to the system configuration that might result in this behaviour. It seems to freeze whether I download POP3 or IMAP and even if I'm only downloading headers it will still freeze.

I get mail from more than one server, and it's doing the same thing on all of them. I've tried removing and reinstalling Thunderbird, but no luck. I've also tried building and installing the package with debugging options, and it still reproduces the same error. I guess it must be a configuration file that's got corrupted somewhere along the line. Any ideas how to fix it? (Naturally access to email is quite crucial for work).

---

### Post by spin2cool on 2006-08-28
You've reinstalled it, but that may not have started you with a clean profile.  IIRC, it's stored in ~/.mozilla-thunderbird  Move the folder to something else, reinstall thunderbird with a fresh profile, and see if the problem persists.

---

### Post by Ndlovu on 2006-08-29
Thanks, spin2cool. I was hoping to keep my profile, but in the end it wasn't too much of a headache to set it all up again. Problem is now solved

---

