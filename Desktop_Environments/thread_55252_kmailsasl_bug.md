---
title: "kmail/sasl bug"
date: 2005-08-08
forum: Desktop Environments
---

### Post by numerodix on 2005-08-08
I've been running ubuntu at work for about a month, among other things I'm using it to connect to a postfix mailserver with tls. It's been working perfectly well up to this point, but as I got back from my vacation today, suddenly it malfunctions. As the title states, this is kmail. As I got to Settings>Configure KMAIL>Account>Sending, then open the server settings and choose the Security tab, click "Check What the Server Supports" I get TLS;PLAIN with no error. But when I send a message, not only do I get *SASL(-4): no mechanism available: No worthy mechs found authentication not supported*, but I also get this is in the console:

```
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libkdecore.so.4: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libkdecore.so.4: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libkdecore.so.4: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libkdecore.so.4: undefined symbol: OpenSSL_add_all_algorithms_noconf

```

Any ideas on how to fix it?

---

