---
title: "OpenSSH - diff btwn guides?"
date: 2009-02-27
forum: General Help
---

### Post by memilanuk on 2009-02-27
Hello,

I recently installed 8.04 LTS server on a small, slightly older machine.  I'd selected the openssh-server option durin install, among others so I am able to log in via ssh now from Terminal.app on my Macbook \\:D/

So now I'm working on setting up to use keys and no passwords for things like rsync, etc.  I was looking at the OpenSSH section of the 8.04 LTS (and 8.10) Server Guide... and it says to generate keys using DSA, and no password (just hit enter when prompted for a password during key generation).  The Advanced OpenSSH Guide says to use RSA, and to be sure and use a *strong* password, as having key files on other computers but not requiring a passwd is "very insecure".

So... which would you recommend following, and why? ;)

TIA,

Monte

---

### Post by adult swim on 2009-02-27
i have always used rsa keys with a strong passphrase.  i guess thats because i learned ssh reading the advanced openssh guide :)  with a strong passphrase it gives you a second layer of defense.  even if someone gets ahold of your keys, they will still need to know the passprase to use them.  
whenever you login with the rsa key, it will ask you for a passprase, and there is an option to add that to your keyring, so whenever you log into ubuntu, the key is already to go when you ssh into your other box, no need for the passprase.

---

