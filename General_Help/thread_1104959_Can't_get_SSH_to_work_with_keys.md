---
title: "Can't get SSH to work with keys"
date: 2009-03-24
forum: General Help
---

### Post by dr_pressure on 2009-03-24
Hi guys,

I'm trying to get ssh to work with keys. Here's what I've done so far:

ssh-keygen -t dsa (on local_machine)
copied the contents of id_dsa.pub into ~/.ssh/authorized_keys2 on remote_machine

According to various sources online I should now be able to log into the remote machine without typing a password. However when I type ssh user@remote it just says "Connection closed by remote"

I have different usernames on both systems, but that shouldn't matter, right?

Any help would be appreciated!

---

### Post by albandy on 2009-03-24
store it in authorized_keys not in authorized_keys2

you should do it this way:
cat id_dsa.pub >> ~/.ssh/authorized_keys

---

### Post by dr_pressure on 2009-03-24
Thanks mate, it's working perfectly now.

Just one thing, does this mean I'm using SSH v1?

---

### Post by Bachstelze on 2009-03-24
> **dr_pressure said:**
> Thanks mate, it's working perfectly now.

Just one thing, does this mean I'm using SSH v1?

No. HOWEVER, you say

> According to various sources online I should now be able to log into the remote machine without typing a password.

So I'm guessing this means you didn't assign a passphrase to your key, right?

This is a bad idea. Very bad. **Never** use an unencrypted key for interactive SSH! Stealing a key is much easier than you seem to think.

---

### Post by dr_pressure on 2009-03-24
Thanks for the heads up HymnToLife, at the moment I'm just testing stuff but when I do this for real I do intend to use a passphrase.

There's one final thing I'm confused about (last question, I promise):

Why can't I specify a different file name instead of authorized_keys?

I've got a separate test sshd running on port 555, the config file is set to /dev/null... and I've started it with -o AuthorizedKeysFile=/publickey

I would expect this to let me log in as any user I want provided I have the correct private key, but instead it doesn't let me log in at all (unless I use a passphrase). Any idea what is going on?!

Thanks!

---

### Post by Bachstelze on 2009-03-24
> **dr_pressure said:**
> I've got a separate test sshd running on port 555, the config file is set to /dev/null... and I've started it with -o AuthorizedKeysFile=/publickey

I would expect this to let me log in as any user I want provided I have the correct private key, but instead it doesn't let me log in at all (unless I use a passphrase). Any idea what is going on?!

It works fine here. Did you put your public key in [font="monospace"]/publickey[/font]?

---

### Post by dr_pressure on 2009-03-24
I just tried it again and for some unknown reason it has decided to start working :):D

Thanks for all the help guys

---

