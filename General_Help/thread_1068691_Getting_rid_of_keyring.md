---
title: "Getting rid of keyring"
date: 2009-02-13
forum: General Help
---

### Post by ooobooontooo on 2009-02-13
I know this has been asked a couple times in the past, but I never found a definite answer.

Every time I try to ssh (rsa-based) or connect to a network the keyring manager pops up. So far, I've been getting around this by killing gnome-keyring-d at startup. Is there a more permanent solution?

Also, if I get rid of the keyring manager, is there another manager that anyone would recommend for storing network keys? I don't like the keyring manager...Also, will anything break if I get rid of it?

Thanks in advance.

---

### Post by ddmdllt on 2009-02-13
Hi,

Which version of Ubuntu are you using? Do you use ssh from the command line or just an application based on ssh?

---

### Post by ooobooontooo on 2009-02-13
hardy 8.04

ssh from command line

EDIT: Also, I know that if I change my keyring password to that of my login, I won't be prompted, but I don't want to do that. I want to get rid of it. I don't feel safe with the fact that the keyring manager has access to ALL my keys during my login session.

---

### Post by ddmdllt on 2009-02-13
Argh, i'm using kubuntu 8.04 and i've not this kind of problem (it's kde, but kdewallet doesn't seem to interfere with ssh).

However, I didn't remind about this kind of problem when I was using ubuntu (with gnome) in the past (older version), and I've not encountered the problem when ssh-ing from my university (recent Ubuntu, 8.10 if I remember right).

---

### Post by _sAm_ on 2009-02-13
I use a keyfile for ssh, and got mad when seahorse asked for a password every time I wanted to use ssh, so I changed the password. 

The keyring(Seahorse) is storing the mainpassword in; 
~/.gnome2/keyrings

If you rename this file to something else it will ask you to set a password next time you use ssh. Dont enter a password at all, just hit enter and it will no longer ask for a password when you use ssh.

---

### Post by ooobooontooo on 2009-02-13
@ddmdllt
Thanks for the reply. I'm kind of thinking switching over to kde myself...

@_sAm_
Can you be more specific as to what that does? Does it just set the keyring password to nothing. If so, I would prefer not to do that.

---

### Post by ddmdllt on 2009-02-21
> **ddmdllt said:**
> I've not encountered the problem when ssh-ing from my university (recent Ubuntu, 8.10 if I remember right).

Yeah, 8.10 with gnome it is. But I don't use ssh keyfiles from there (from my university's computers).

In fact I use either the password method (without authenticating the client by a keyfile) or the keyfile method (but I don't use a password in this case). I don't directly associate passwords to keyfiles (but I don't have keyfiles that give me root access directly).

> **ooobooontooo said:**
> @ddmdllt
Thanks for the reply. I'm kind of thinking switching over to kde myself...


I'm not sure it is a real solution for your problem. KDE is a very nice desktop environment, really different from gnome (which is nice too); but if you consider switching for just this reason, you may have missed the point.

---

### Post by ooobooontooo on 2009-02-23
Haha. Yes, I'm not switching to KDE just for this reason. I've been looking at some of the images and videos of KDE and they look for very nice.

---

