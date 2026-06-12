---
title: "Evolution and GnuPG Error"
date: 2005-12-28
forum: General Help
---

### Post by OlineSixtyOne on 2005-12-28
I have GnuPG and Evolution set up on my computer. Whenever I try to send a message encrypted with GnuPG I get this error:
> Could not create message.
Because "Failed to execute gpg: Broken pipe", you may need to select different mail options.
Help me please!

---

### Post by OlineSixtyOne on 2005-12-28
I also get this when decrypting from the command line using gpg -d [file-name].

---

### Post by OlineSixtyOne on 2005-12-29
bump

---

### Post by Prefader on 2005-12-29
Not  knowing how experienced you are with Evolution and GnuPG, and being completely new to GnuPG, and encryption, myself . . .

I had the same error message, it resolved itself after I imported the mail recipient's public key (didn't realize that I hadn't imported it yet when I tried to send the message.)

Maybe that helps some?

---

### Post by OlineSixtyOne on 2005-12-29
Thanks, that fixed it.

---

### Post by OlineSixtyOne on 2006-01-05
Umm I'm having the problem again. I imported the key, and it gives me the error when sending it to someone.

---

