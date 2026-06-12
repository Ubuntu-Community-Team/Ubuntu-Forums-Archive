---
title: "Full-system encryption without authentication"
date: 2009-04-25
forum: General Help
---

### Post by Botond on 2009-04-25
[INDENT]Hi There,

does somebody know a way how to create a server with ordinary root filesystem encryption but without the usual boot-time authentication? I'd like to have a server which can be given to an untrusted party, he can then boot it up and use its services (samba, or imap or alike)  but can't modify the server.[/INDENT]
[INDENT]I was thinking of using encrypted initrd which would contain the usual startup code for using an encrypted root filesystem and which would also contain the keys for this filesystem so that the kernel wouldn't need the extra authentication step. I just haven't found instructions on how to use encrypted initrd.[/INDENT]
[INDENT]Plain unencrypted initrd would also be OK if the kernel would contain the keys for the root filesystem. I know that such protection isn't bulletproof and some smart guys could disassemble the kernel and find the keys (either for initrd or the root filesystem) but I don't want to hide the server from the CIA only from script-kiddies.
Thanks for any help.[/INDENT]

---

