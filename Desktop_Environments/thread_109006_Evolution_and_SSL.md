---
title: "Evolution and SSL"
date: 2005-12-27
forum: Desktop Environments
---

### Post by dpm on 2005-12-27
Hi there,

I've got a general question to any e-mail gurus out there.

I've set up a POP3 account in Evolution, which is working fine at the moment. I've also set up security for this account by choosing *Use Secure Connection: **Always*** under its POP3 properties. The same settings also apply for SMTP. 

Seeing that, for example, Thunderbird has got an option for TLS and one for SSL under the same security settings, 

**1.-** Which security protocol does Evolution use in this case, SSL or TLS?

Also, seeing that there are also settings for secure authentication, I'm not sure whether choosing *Use Secure Connection: **Always*** implies that all communication with the SMTP server is encrypted or whether authentication is handled somehow differently. 

Since I did not know and I didn't want my password to be sent as plain text, I set up Evolution to handle authentication with CRAM-MD5 for SMTP and APOP for POP3. Both are supported types from the server which holds my free e-mail account.

So far, everything works.

Anyway, my question is whether using a secure authentication method is needed at all when choosing *Use Secure Connection: **Always ***in Evolution. My guess is that I can choose PLAIN text as authentication method without worries, since the username and password will ultimately be sent in a secure way by the underlying (I assume) SSL protocol. The secure authentication methods are there only (another guess) in case the server does not offer a secure connection with e.g. SSL. Therefore my question is:

**2.-** When using a secure connection (*Use Secure Connection: **Always*** option in Evolution) is the authentication also handled by the secure connection, or is it necessary to use a secure authentication method additionally?

Thanks.

---

