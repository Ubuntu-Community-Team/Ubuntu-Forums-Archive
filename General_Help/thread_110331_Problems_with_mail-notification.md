---
title: "Problems with mail-notification"
date: 2005-12-30
forum: General Help
---

### Post by juantxorena on 2005-12-30
Greetings to all.

I'm using Thunderbird as email client for my 2 email accounts, and I want a system tray mail notificator. I don't like the plugin for thunderbird (I can't remember its name), because thunderbird must be always opened in order to make it work. So I choosed mail-notification.

I have one POP email accounts, and a gmail account, configured as a POP account (to use with email clients like thunderbird).

The problem:

The non-Gmail account works properly. The Gmail account, if I configure it as a Gmail account on mail-notification, the tray icon appears, saying that I have 20 new messages on Gmail account, which is false. I suposses that mail-notification "log in" the web client of Gmail, which I never use it, and show me the last 20 mails in my inbox, which are marked as no-read because I never log in in the web client of Gmail (sorry for the confusing paragraph).

P.D. Sorry for my english :oops:

---

### Post by juantxorena on 2005-12-31
Nobody?

---

### Post by kaamos on 2005-12-31
This is why imap is much more convenient than pop. I at least do not know a way to do what you wish with a pop account. It say at gmails pages that they do not *yet* support imap..

---

### Post by juantxorena on 2005-12-31
I can't choose the type of my accounts, sorry :P

I've just purged mail-notification (like uninstall but removing conf files). I installed it again via apt-get, but the preferences and accounts were untouched, so the conf files weren't removed (why?).

BTW, I purged it again, and I installed mail-notification manually: I downloaded  openSSL tarball and installed it, everything went OK. The I installed mail-notification from the tarball, configuring it with SSL support. The last lines of configure result:
```
POP3 and IMAP features
  --enable-ssl                 yes
  --enable-sasl                no (Cyrus SASL not found)
  --enable-ipv6                yes

```
After making and installing it, I can't choose SSL options when creating an account, so GMail account doesn't work (the same error as above).

Ideas?

---

