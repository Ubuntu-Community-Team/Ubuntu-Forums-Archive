---
title: "Seahorse problems anyone?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by pjstadig on 2005-10-20
I've installed seahorse, and it has worked great for creating a key pair and importing public keys from keyservers, but when I try to sign a public key that I downloaded from a keyserver it says "Couldn't sign key general error"

Any ideas?

Paul

---

### Post by pjstadig on 2005-10-20
I've also had the same problem with gpa, btw. Is this a problem with gpg? I find it highly suspect that both gpa and seahorse would give "general error" when I try to sign a key.

Thanks for any help.
Paul

---

### Post by Pizon on 2005-10-21
I just ran into the same problem using seahorse however when I used gpg --sign-key from the commandline it worked as expected.  I then launched seahorse from a gnome-terminal window and attempted to sign another key.  I noticed the following output in the terminal window:

** (seahorse:6560): CRITICAL **: file seahorse-key-op.c: line 369 (sign_transit): should not be reached

** (seahorse:6560): CRITICAL **: edit_key: assertion `GPG_IS_OK (err)' failed

Perhaps the answer to our problem lies within...

---

