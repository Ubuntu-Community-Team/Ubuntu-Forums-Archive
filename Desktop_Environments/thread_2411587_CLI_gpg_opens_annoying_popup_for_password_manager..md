---
title: "CLI gpg opens annoying popup for password manager. How do I just get normal CLI?"
date: 2019-02-01
forum: Desktop Environments
---

### Post by david503 on 2019-02-01
On the CLI I type:

```

gpg -c somefile.txt

```

It opens a popup for the password manager.  

So I googled around for how to stop it and get a password prompt on the cli like normal and got to this:

[https://superuser.com/questions/520980/how-to-force-gpg-to-use-console-mode-pinentry-to-prompt-for-passwords](https://superuser.com/questions/520980/how-to-force-gpg-to-use-console-mode-pinentry-to-prompt-for-passwords)

Well it gets worse; there is no gpg.conf. 

```

$ ls -al /home/bog/.gnupg/
total 20
drwx------  3 bog bog 4096 Feb  1 00:10 .
drwxr-xr-x 39 bog bog 4096 Feb  1 00:10 ..
drwx------  2 bog bog 4096 Dec 31 06:30 private-keys-v1.d
-rw-------  1 bog bog   32 Feb  1 00:05 pubring.kbx
-rw-------  1 bog bog  600 Feb  1 00:12 random_seed

```

Please help.

Ubuntu MATE 18.04.1

thanks

---

