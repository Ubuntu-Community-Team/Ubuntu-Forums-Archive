---
title: "Evolution signature validation problem"
date: 2008-12-15
forum: General Help
---

### Post by rileinc on 2008-12-15
This problem occurred to me while I was weighing between Thunderbird and Evolution. 

To carry out my own little test, I use 2 Gmail accounts (IMAP) and 2 GPG keys, one key per email. One account uses Thunderbird, the other uses Evolution. I send and receive messages using both clients with the following parameters:
1. Signed.
2. Signed and encrypted.

With signed-only messages, both clients had no trouble validating.

With signed *and* encrypted messages, however, Evolution (on the receiving end) indicates the message is encrypted but *not* signed. 

I've ruled out personal omission because the same messages in Thunderbird's "Sent" folder is shown as signed and encrypted. I've repeated the test multiple times.

Is this a bug or am I doing something wrong here?

---

