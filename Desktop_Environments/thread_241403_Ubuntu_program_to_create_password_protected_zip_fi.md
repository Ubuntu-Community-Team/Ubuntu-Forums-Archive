---
title: "Ubuntu program to create password protected zip files"
date: 2006-08-22
forum: Desktop Environments
---

### Post by jonboy99 on 2006-08-22
First of all - i'm aware that winzip password protection is weak and easily broken, but need it to stop casual snoopers from reading email attachments that have been sent to an email address which is shared between several people.
The person I am sending them to has no install privileges on a windows machine at all and only winzip already installed.

With winzip in windows I can put a password on a zipped file easily, but ARC doesn't give me this option that I can see.  Is there an alternative program for ubuntu that does?

Cheers
Jon

---

### Post by kwalo on 2006-08-22
> **jonboy99 said:**
> 
With winzip in windows I can put a password on a zipped file easily, but ARC doesn't give me this option that I can see.  Is there an alternative program for ubuntu that does?

Maybe gpg might interest you. You and your friend might use thunderbird, or sylpheed, to encrypt your e-mail messages. This is much more secure than zip passwords.

You can also type in the following commands:

If you want to create a simple passphrase-protected data on a file foo, you would use the follownig command:```
gpg --output foo.gpg --symmetric foo
```and enter the passphrase.

To encrypt with user's public key (You need to add a user's key to your keyring), use the following command:```
gpg -d foo
```
and follow the instructions.

Decrypting is a simple command```
gpg --output foo -d foo.gpg
```
Gpg is availabe for Windows also, so your friend might ask administrator to install it on a Windows machine.

---

### Post by mkljun on 2006-11-19
This link might interest you:

[http://www.linuxjournal.com/article/9370](http://www.linuxjournal.com/article/9370)

Using zip -P or -e options in command line.

---

### Post by jonboy99 on 2006-11-19
That's exactly what I wanted mkljun - wasn't expecting a reply to this thread now! \\:D/

---

