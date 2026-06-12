---
title: "unknown password for default keychain"
date: 2011-09-13
forum: Desktop Environments
---

### Post by mttolmie on 2011-09-13
I do not know the password of my keychain.
My system is 10.04.3 amd 64
To isolate my problem I installed a fresh copy of 10.04 in an unused partition. I brought over a copy of .ssh, nothing else.
On the command ssh xxx.xxx.xxx.xxx I get a dialog box asking for a password because the .pub is locked. Tried my login password, blank, the passphrase of the rsa key.
It turns out that Lucid on its own has given me a keyring and a ssh-agent but it did not tell me what the password is:(
I there an mistunderstanding on my part what password this?
Attempts to change the password of course failed because you have to know the old password.
If this was answered before, my apologies, but please tell me the magic incantation to locate such a thread.

---

### Post by mikewhatever on 2011-09-13
There is no default password. It may not be entirely clear, but the keyring prompt asks to set a password, or use unsafe storage if you leave the password field blank.

---

### Post by mttolmie on 2011-09-13
This is what the dialog box says:

[I]Enter password to unlock the private key

An application wants access to the private key 'blah@blah-2.local', but it is locked[/I]

That certainly does not look like asking me to set a password; it wants me to give the password.

---

### Post by mttolmie on 2011-09-13
Forget my query. 
After the answer that the default chain does not have a password, I once more checked my pass phrases: one got stepped upon in transfer.
Sorry for raising the issue.

---

