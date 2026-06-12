---
title: "[Citadel][Fetchmail]Question on Fetchmail and LMTP"
date: 2011-12-21
forum: Desktop Environments
---

### Post by blenderfox on 2011-12-21
I have a quick question. I use Fetchmail to download my gmail account emails and pass them onto Citadel via LMTP. This works but Citadel rejects the emails because Fetchmail does not provide SMTP authentication. Is there a way I can tell Fetchmail via the fetchmailrc file to login using a user and pass (different from the gmail one) when attempting to forward internally. I couldn't find anything obvious in the man pages.

Example: I might be authenticating as "bloggsj@gmail.com" on gmail, but I have to authenticate as "jbloggs" on Citadel, and with a different password. To work around this, I had to set Citadel to allow Unauthenticated SMTP, which I really don't want to have to do, if I can help it.

---

