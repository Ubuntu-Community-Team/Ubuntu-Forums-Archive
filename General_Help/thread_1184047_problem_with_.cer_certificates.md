---
title: "problem with .cer certificates"
date: 2009-06-10
forum: General Help
---

### Post by tranceporter on 2009-06-10
Hi All,

I have two certificates: issuer cert and user cert. User cert is protected with password. When installing in MSIE password is accepted and cert is installed and site can be viewed, but when installing in Firefox in Ubuntu - i get error: "Failed to decode the file.  Either it is not in PKCS #12 format, has been corrupted, or the password you entered was incorrect."
Well, it's not *.p12 but still is recognized as cert when i use
openssl x509 -in customer.cer -noout -text -inform DER

Response is attached.

I exported from IE these certs to PKCS #12 format, but still in ubuntu certs are not accepted.

Any help how to install it?

Regards

---

### Post by tranceporter on 2009-06-14
Really noone knows a bit about certs?

---

