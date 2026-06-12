---
title: "how to sign code of conduct."
date: 2005-12-31
forum: General Help
---

### Post by jsmidt on 2005-12-31
I want to sign a code of conduct.  I have used gpg to generate a public and private key.  Now that I have those how do I sign the code of conduct?  Thanks. :)

---

### Post by earobinson on 2005-12-31
is it the ubuntu code of conduct you are looking to sign?

[https://launchpad.net/codeofconduct/1.0](https://launchpad.net/codeofconduct/1.0)

---

### Post by jsmidt on 2005-12-31
yes, do I just download it do gpg  --clearsign doc.  Then submit it on launchpad?  Or is there something else.

---

### Post by earobinson on 2005-12-31
That link has everything you need... unless im missing something

> GPG Signed Code of Conduct. It should contain a clearsigned copy of current Code of Conduct version (use: `gpg --clearsign`).
[https://launchpad.net/codeofconduct/1.0/+sign](https://launchpad.net/codeofconduct/1.0/+sign)

EDIT: guess i am dident work for me

---

### Post by az on 2005-12-31
[https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)

GPG Keys and Launchpad You need to tell Launchpad about your GPG key(s) to be able to sign the Ubuntu Code of Conduct (and thus become an Ubuntite) and to build packages using HCT.

Visit the GPG Keys page once logged into launchpad. Paste your key fingerprint into the textbox:

gpg --fingerprint

Example: the key fingerprint would be something like "95BD 8377 2644 DD4F 28B5 2C37 0F6E 4CA6 D8FC 66D2"

Launchpad will send you and email which you will have to decrypt. You can save the text to a file and run

gpg --decrypt file.txt

You will need to enter your passphrase.

The message will be displayed along with the link you must follow to confirm your key in launchpad.

Follow it, enter your launchpad password as asked and you are done!

---

### Post by jsmidt on 2005-12-31
thanks azz for listing all the steps.

---

### Post by az on 2005-12-31
It's all on the wiki.

---

