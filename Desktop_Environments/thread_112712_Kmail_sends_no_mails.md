---
title: "Kmail sends no mails"
date: 2006-01-04
forum: Desktop Environments
---

### Post by teclis on 2006-01-04
I have installed kmail. Imap works fine. Sending mails with evolution works without any problems.

Sending mails with kmail fails; the mails stay in the outbox. No error message was shown. In the SMTP-Tab of kmail I got an error, if click on the "check what the server supports"-Button. The following message appears instantly: "Could not read ." This functions works in evolution without any problems.

No, I don't want to use evolution... ;)

Maybe I have forgotten to install something?

Teclis

---

### Post by Sef on 2006-01-05
Have you checked what you imputted to make sure you imputted everything correctly?

---

### Post by teclis on 2006-01-05
[QUOTE=Sef]Have you checked what you imputted to make sure you imputted everything correctly?[/QUOTE]
I wiped out my complete .kde in my Home and started again. Kmail ist still not working.

I think kmail has a general problem talking with SMTP-Servers. How can I get more useful information, what kmail is doing in the background?

Update:
I got some more informations from kmail:
```

kmail: ERROR: : couldn't create slave : Aufruf des Ein/Ausgabe-Moduls nicht möglich.
klauncher meldet: Unknown protocol 'smtp'.
kmail:

```

**Solution:**
Package kdebase-kio-plugins was missing. No problems anymore

---

