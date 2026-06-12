---
title: "What key file formats does GPG know about?"
date: 2009-06-23
forum: General Help
---

### Post by bogdanbiv on 2009-06-23
I'm trying to import existing putty ssh keys in Ubuntu. This topic has already been asked in [Howto import existing putty ssh keys into seahorse?]("http://ubuntuforums.org/showthread.php?t=471485") and [Need help using existing putty ssh keys with seahorse]("http://ubuntuforums.org/showthread.php?t=474162").

Solutions to it seem to amount to:
```
Putty comes with software to convert it. Check out puttygen.
Load key and export.
```

But the problem is very much unsolved for me, since I exported my keys from Puttygen to openssh and ssh.com formats plus the native file format, but when I try to import them in a keyring manager (KGPG or Seahorse) I get this answer:
KGPG answers:
[GNUPG:] NODATA 1
[GNUPG:] IMPORT_RES 0 0 0 0 0 0 0 0 0 0 0 0 0 0
Seahorse answers:
file:///media/KINGMAX/PKI_cert/sign_private_3.openssh: Invalid file format

As far as I can tell, Seahorse and KGPG seem just frontends to GnuPG, so what works with one works with all keyring managers, right?

So what key file formats does GPG know about?

---

### Post by bogdanbiv on 2009-06-24
UPDATE:
Tried from the command line:
Of course GNU PG does not accept the files, it has nothing to do with frontends, which are just a thin layerer over GPG:

```
user@user-laptop:/media/KINGMAX/PKI_cert$ gpg --import encrypt_private_3.openssh
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
user@user-laptop:/media/KINGMAX/PKI_cert$ gpg --import encrypt_private_3.ppk
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
user@user-laptop:/media/KINGMAX/PKI_cert$ gpg --import encrypt_private_3.ssh_com
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

As far as I can understand from: [Re: Import *.p12 Keys into GnuPG fails]("http://marc.info/?l=gnupg-users&m=108997213420448&w=2"), which is:
```
> How can I convert the P12-format into OpenPGP?

You can't pkcs#12 is usually used for X.509 key s which are not
compatible with OpenPGP keys.  

gnupg 1.9 comes with support for X.509/CMS, though.
```

It seems that I have to transfer my SSH keys into pcks#12/X.509 certificate format. Or maybe I should start with a x.509 certificate and make ssh key pairs from it.

I'll come with updates as soon as I can.

---

### Post by bogdanbiv on 2009-06-24
It seems that ssh could not read from the private key file exported by PuttyGen in OpenSSH format. Also OpenSSH should be able to export ssh keys into RFC 4716, but I don't know what's wrong with that either.

So, I turned the problem on it's head:
I generated the key pair using ssh-keygen and imported the private key in PuttyGen, from there I generated again the public key.

ssh-keygen -t dsa -C "Bogdan Bivolaru <bogdan.bivolaru@gmail.com>, 20090624" -N YOUR_PASSWORD

Be careful because if you do this the password remains stored in clear in the bash history. This is dangerous because anyone who can read your bash history can learn your secret SSH password. So clear your bash history or find a better way to input that password!

---

