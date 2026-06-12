---
title: "GnuPG Problem"
date: 2005-08-01
forum: Desktop Environments
---

### Post by gmc on 2005-08-01
Greeting Folks,

I've been on the ubuntu-security-announcements mailing list for a while now and the one thing that bothered me was being told by evolution that the gnupg signature for announcements from Martin Pitt could not be verified. So I tried the following:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 0x5E0577F2

Now I get a message (see attached gif file)

Can anyone shed some light on how to fix this problem?

G.

---

### Post by jdodson on 2005-08-01
right, this is a standard error that basically means, "hey we are not 100% sure this guy is who he says he is,"

basically you have to make that key trusted in some fashion.  read up in gpg about that.

---

### Post by nocturn on 2005-08-02
This error means that the signature is not signed by a signature you trust.
The signature can have 1000 signatures, but if none of them is trusted by you, this is the result.

To fix it you can sign it yourself (local if you don't want to upload it).
'man gpg' shows how to do this, or use something like seahorse (GUI).

---

### Post by nocturn on 2005-08-02
Signed PGP keys are part of 'The web of trust', a good explanation is here:
[http://www.rubin.ch/pgp/weboftrust.en.html](http://www.rubin.ch/pgp/weboftrust.en.html)

---

### Post by gmc on 2005-08-02
Thanks Folks. Looks like I've got some reading to do.

G.

---

