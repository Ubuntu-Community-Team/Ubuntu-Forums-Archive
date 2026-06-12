---
title: "kmail will not icluded gpg key"
date: 2005-10-19
forum: Desktop Environments
---

### Post by JvdS45 on 2005-10-19
I tried to use gpg key in kmail but i get message: "not found any backends for finding the key control yopur installation"

---

### Post by JvdS45 on 2005-10-19
[QUOTE=JvdS45]I tried to use gpg key in kmail but i get message: "not found any backends for finding the key control your installation"who can help me to resolve this problem

---

### Post by GeneralZod on 2005-10-19
Ensure your system is fully up-to-date (the default install of Kubuntu was missing GPG integration with kmail, but there was a KDE update yesterday) and maybe install kgpg, too.

---

### Post by drx on 2005-10-19
I did install the new packages, but still i cannot decrypt messages. Instead the mail window shows

"Nicht entschlüsselbare Daten nicht angezeigt."
(Not decryptable data is not displayed.)

If a message is just signed, it works perfectly. Both Crypto Modules (openGPGP and S/MIME) are activated and reported no errors. KGPG also works as far as i can tell, an enigmail in Mozilla-Thunderbird works as well.

So were these updates i got today the ones that should fix the kmail GPG working together? Is there something i made wrong?

---

### Post by shrink on 2005-11-21
i'm new to all this but have been having the same problems with kmail and kgpg.  i've managed to get it setup so that i can sign and encrypt outgoing messages, and can recognise incoming signatures, but when i'm sent messages encrypted with my public key i can't decrypt them. i get a message saying  'error:bad passphrase ' except i haven't been asked to enter my passphrase. i also get the same thing if i try to read my outgoing encrypted messages from my sent messages folder. same error.

anyone got any ideas?

cheers

---

### Post by karl_kashofer on 2005-11-24
Same problem here, seems gpg-agent is not running

---

