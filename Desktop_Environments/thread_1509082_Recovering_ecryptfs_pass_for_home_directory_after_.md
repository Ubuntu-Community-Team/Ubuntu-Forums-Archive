---
title: "Recovering ecryptfs pass for /home/ directory after fresh Ubuntu install"
date: 2010-06-13
forum: Desktop Environments
---

### Post by coderam on 2010-06-13
I'm trying to recover my /home/ directory passphrase.

Here's what happened:

1. I ran a fresh Ubuntu install (10.04) and selected the option to "encrypt home directory"
2. I rebooted after the Ubuntu install and was prompted about writing down my encryption passphrase
3. ** I didn't write down the passphrase or the command for viewing the passphrase

Does anyone know the command for viewing the passphrase?

---

### Post by coderam on 2010-06-13
I figured this out: 

[email]user@svn:~/.ecrypt[/email]fs$ sudo ecryptfs-unwrap-passphrase wrapped-passphrase 

This prompts you for a password and then shows you your passphrase

---

