---
title: "How do i import an ssh private key?"
date: 2009-06-20
forum: General Help
---

### Post by gareth0 on 2009-06-20
I exported an ssh key using seamonkey, this produced a file starting with:

> -----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,98E17006CCCC08F9

When I try importing this file in seamonkey (on a different machine), seamonkey says "imported keys" but the key has *not* been imported.

How do I import the key from this file? I do not have the original key files from ~/.ssh/.

Thanks

---

### Post by gareth0 on 2009-06-20
For any other poor bastards trying to use seamonkey, I managed to fix it by:

1. creating ~/.ssh/id_rsa and copying the ascii private key from above to it.
2. creating ~/.ssh/id_rsa.pub and copying into it the output of "ssh-keygen -e -f id_rsa", then editing it so it looks like a regular id_rsa.pub file...

---

### Post by junico on 2011-06-03
thanks for the clue!! i use 'seahorse'  and almost gave up all hopes to import my keys..
would like to add that it's not really necessary to rename the file..  having appropriate public key is enough..

..and 'ssh-keygen -y -f ~/.ssh/private_key > ~/.ssh/public_key' creates regular public_key - no needs to edit..

---

### Post by s.fox on 2011-06-03
Thread Necromancy.

Thread Closed.

---

