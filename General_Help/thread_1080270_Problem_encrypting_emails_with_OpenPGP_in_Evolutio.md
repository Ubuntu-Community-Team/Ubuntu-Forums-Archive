---
title: "Problem encrypting emails with OpenPGP in Evolution"
date: 2009-02-25
forum: General Help
---

### Post by meho_r on 2009-02-25
Hi,

Why can't I encrypt emails in Evolution using OpenPGP? Every time I try, all I got is this error:

```

Could not create message.

Because "gpg: using PGP trust model
gpg: using subkey xxxxxxxx instead of primary key yyyyyyyy
gpg: xxxxxxxx: There is no assurance this key belongs to the named user
gpg: [stdin]: encryption failed: unusable public key
", you may need to select different mail options.

```

1. I created my key using SeaHorse wizard
2. Public key of the person I'd like to send an email is created in Seahorse too and exported through "Export Public Key"
3. I imported given public key in Seahorse (I even tried deleting it and retrieving it again from a public keyserver).

So, it's standard procedure. What's wrong with Evolution? Any ideas?

BTW, in Thunderbird it works fine.

---

### Post by meho_r on 2009-02-25
...and can't use Thawte certificate for encryption too :( This is getting on my nerves, really... Don't have to mention that in Thunderbird no problem with s/mime too.

---

### Post by Ehknaton on 2010-11-12
Tticking "Always trust keys in my keyring when encrypting" should solve your problem, in the Security Tab, where you set your PGP ID.

---

