---
title: "Setting Up SSL"
date: 2006-07-19
forum: Desktop Environments
---

### Post by sparty2809 on 2006-07-19
Ok, I installed the LAMP Server from the Ubuntu 6.06 disk.  I got my crt file back from godaddy.  Now how do I set it up?  I tried putting the 
```
SSLCertificateFile /etc/apache2/ssl/ssl.csr/website.csr
SSLCertificateKeyFile /etc/apache2/ssl/ssl.key/website.key
SSLCertificateChainFile /etc/apache2/ssl/ssl.crt/website.crt
```

in the ssl.conf file, but it doesn't work.  I get this error: "Error Code: -12281"

Does anyone know a step by step process?  I have found a lot on self signed ones, but I don't think it's the same steps.

---

### Post by cptnapalm on 2006-07-19
Error Code: -12281 is the error that Apache gives?  Or the browser?

While I can't help out too much, as I've never really gotten Apache SSL to work quite right, I did a bit of digging and found some sites which *may* be of help.

Redhat centric, but possibly adaptable: [http://www.freessl.com/resources/install/chainedssl/apache_install.htm](http://www.freessl.com/resources/install/chainedssl/apache_install.htm)

[http://www.webservertalk.com/archive54-2004-12-653525.html](http://www.webservertalk.com/archive54-2004-12-653525.html)

---

### Post by sparty2809 on 2006-07-19
That is what the browser says.  I will check out those links.  Thanks.

---

### Post by sparty2809 on 2006-07-19
This is the error I get in the log:

```
[Wed Jul 19 12:44:24 2006] [error] Init: Unable to read server certificate from file /etc/apache2/ssl/ssl.crt/
ssl.crt
[Wed Jul 19 12:44:24 2006] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHE
CK_TLEN:wrong tag
[Wed Jul 19 12:44:24 2006] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITE
M_EX_D2I:nested asn1 error
```

---

